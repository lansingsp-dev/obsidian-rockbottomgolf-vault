# 🧪 BigCommerce Theme Preview on Netlify

## ✅ Goal
Deploy a static version of your custom **BigCommerce theme** to **Netlify**, allowing stakeholders to preview layout/design changes without requiring a local server or exposing your production store.

---

## 🧰 Prerequisites
- Node.js and `stencil-cli` installed
- A bundled BigCommerce theme (`stencil bundle`)
- Free [Netlify account](https://app.netlify.com/signup)

---

## 🧱 Step 1: Bundle Your Theme

```bash
cd your-theme-folder
stencil bundle
unzip stencil.zip -d theme-preview
cd theme-preview
```

After this, you should have:
- `assets/`
- `templates/`
- `lang/`
- `content/`

---

## 🧪 Step 2: Create a Static Preview Page

> [!info]  
> Netlify needs an `index.html` file in the root of the deployed folder to serve as the landing page.

1. In the `theme-preview/` folder, create a file named `index.html`.

2. Paste the following content:

```html
<!DOCTYPE html>
<html>
<head>
  <meta charset="UTF-8">
  <title>Theme Preview</title>
  <link rel="stylesheet" href="assets/css/theme.css">
  <style>
    body { font-family: sans-serif; margin: 2rem; }
    header, footer { background: #f3f3f3; padding: 1rem; }
    .product-grid img { width: 200px; margin: 1rem; }
  </style>
</head>
<body>
  <header>
    <h1>BigCommerce Theme Preview</h1>
  </header>

  <section class="product-grid">
    <h2>Sample Products</h2>
    <img src="assets/img/sample-product.jpg" alt="Product 1">
    <img src="assets/img/sample-product.jpg" alt="Product 2">
  </section>

  <footer>
    <p>Note: This is a static preview of your custom theme.</p>
  </footer>
</body>
</html>
```

> [!tip]  
> Use any existing image from your theme (or add one manually) to `assets/img/sample-product.jpg`.

---

## 🚀 Step 3: Deploy to Netlify (Manual Method)

> [!info]  
> This will give you a publicly accessible preview link to share with stakeholders.

1. Go to [https://app.netlify.com](https://app.netlify.com)
2. Click **“Add new site” → “Deploy manually”**
3. Drag and drop the entire `theme-preview/` folder into the upload area

Netlify will provide a public URL like:

```
https://your-preview-site.netlify.app
```

You can now share this URL with your reviewers.

---

## 🔒 Step 4: Add Optional Password Protection

1. In your Netlify site dashboard, go to:  
   **Site Settings → Access Control**

2. Enable **Password Protection**

This will require anyone visiting the site to enter a password before viewing the theme preview.

---

## 🔁 Step 5: Update the Preview

When you make updates to your theme:

```bash
stencil bundle
unzip stencil.zip -d theme-preview
```

Then either:
- Re-upload the folder manually to Netlify  
- Or use the Netlify CLI for faster deploys (see below)

---

## ⚡ Optional: Use Netlify CLI for Fast Deploys

```bash
npm install -g netlify-cli
netlify login
netlify deploy --dir=theme-preview --prod
```

This will push your updated preview directly from the command line.

---

## ✅ Summary

| Step                          | Description                                  |
|-------------------------------|----------------------------------------------|
| Bundle theme                  | `stencil bundle` + unzip                     |
| Create static preview page    | `index.html` with basic layout               |
| Upload to Netlify             | Manual drag-and-drop or CLI-based deploy     |
| Optional: password protection | Restrict access with basic auth              |
| Optional: CLI                 | Automate deploys with `netlify deploy`       |

---

## 📌 Notes

- ✅ Great for layout/design review  
- ❌ No cart, checkout, or dynamic behavior  
- 🔄 Can be extended later with proxy-based staging or ThemeBridge-style functionality
