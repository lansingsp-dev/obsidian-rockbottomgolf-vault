# 🧵 PulseID Custom Widget Setup for BigCommerce

This guide walks you through integrating a custom PulseID embroidery/personalization widget directly into your BigCommerce Stencil theme using Handlebars, JavaScript, and PulseID APIs.

---

## ✅ 1. Handlebars Widget HTML

Place this in a file like `templates/components/products/custom/customizer.html`:

```handlebars
<div id="pulseid-customizer" class="customizer-container">
  <h3>Customize Your {{product.title}}</h3>

  {{#if product.options}}
    <div class="customizer-fields">
      <label for="custom-text">Text to Embroider:</label>
      <input type="text" id="custom-text" name="custom-text" maxlength="20" placeholder="Enter name or message" />

      <label for="text-color">Text Color:</label>
      <select id="text-color" name="text-color">
        <option value="black">Black</option>
        <option value="white">White</option>
        <option value="red">Red</option>
      </select>
    </div>
  {{/if}}

  <div id="custom-preview" class="preview-box">
    <p>Preview will appear here</p>
  </div>

  <button id="apply-customization" type="button">Apply Customization</button>

  <!-- This field gets submitted with the cart -->
  <input type="hidden" name="PulseIDDesignJSON" id="PulseIDDesignJSON" />
</div>
```

Include in `standard-view.html` like:

```handlebars
{{> components/products/custom/customizer}}
```

---

## ✅ 2. Add JavaScript Logic

Create `assets/js/custom/pulseid-widget.js`:

```js
document.addEventListener('DOMContentLoaded', () => {
  const textInput = document.getElementById('custom-text');
  const colorSelect = document.getElementById('text-color');
  const previewBox = document.getElementById('custom-preview');
  const applyButton = document.getElementById('apply-customization');
  const hiddenInput = document.getElementById('PulseIDDesignJSON');

  const variantId = window.PulseIDVariantId || '02BBYCHILCT11111111BBS01';
  const pulseIdApiUrl = `/pulseid/api/api/Designer/GetProduct?variantId=${variantId}`;

  applyButton?.addEventListener('click', async () => {
    const customText = textInput.value.trim();
    const textColor = colorSelect.value;

    if (!customText) {
      alert("Please enter some text to embroider.");
      return;
    }

    const designData = {
      variantId,
      customText,
      textColor,
    };

    hiddenInput.value = JSON.stringify(designData);

    previewBox.innerHTML = `
      <div style="font-size: 24px; color: ${textColor}; border: 1px solid #ccc; padding: 10px;">
        ${customText}
      </div>
    `;

    try {
      const response = await fetch(pulseIdApiUrl);
      if (!response.ok) throw new Error('Failed to fetch product');
      const productData = await response.json();
      console.log('PulseID product data:', productData);
    } catch (err) {
      console.error('PulseID error:', err);
    }
  });
});
```

---

## ✅ 3. Load Script in Theme

In `templates/layout/base.html` or `standard-view.html`:

```handlebars
<script src="{{cdn 'assets/js/custom/pulseid-widget.js'}}"></script>
```

Make sure it's included in your Webpack bundle if needed.

---

## ✅ 4. Proxy PulseID API (Dev Only)

In `stencil.conf.cjs`:

```js
module.exports = {
  proxy: {
    '/pulseid': {
      target: 'https://stagerockbottom.pulseidconnect.com',
      changeOrigin: true,
      pathRewrite: { '^/pulseid': '' },
      secure: false,
    },
  },
};
```

Restart stencil:

```bash
stencil start
```

---

## ✅ 5. Optional: Use PulseID JS SDK (if provided)

```js
const configObject = new StitchEngine.SEConfigObject("https://stagerockbottom.pulseidconnect.com");
const factory = new StitchEngine.SEFactory(configObject);
const renderer = factory.getImageRenderer();

renderer.render({
  containerId: 'custom-preview',
  text: customText,
  color: textColor,
  variantId: variantId,
});
```

---

## 🛒 6. Customization Data in Cart

The hidden field `PulseIDDesignJSON` will be posted along with the Add to Cart form.

- You can also use line-item customizations via the Storefront API if needed.
- Consider encoding this data as part of a product modifier if the logic becomes more complex.

---

## ✅ Summary

| Step | Action |
|------|--------|
| Handlebars | Add UI for text input, color selector, and preview |
| JavaScript | Capture user input and serialize into JSON |
| PulseID API | Call API to load config and preview |
| Cart | Pass hidden field into BigCommerce cart |
