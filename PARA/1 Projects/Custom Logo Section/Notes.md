- PulseID API - https://rockbottom.pulseidconnect.com/api/home/index
- A template will also give you more control.
- RBG gives a lot of flexibility when using the personalization widget.
	- Can create multiple lines of text using by duplicating the text to a new line.
	- Can add a design in between the 2 lines of text
	- ![[Pasted image 20250722083023.png]]
- The problem with using the Freeform Designer widget and being too open with flexibility with what you can do with the RBG site is you have no control over what they can do and how to charge for it.
- If you enforce a template/style like the Callaway site then you have tight control over what can be created and charged. Their site is built in with the cost as you select a template.
- What is nice with Callaway site is that you can show real time pricing depending on the template selected. Will we have to use APIs over the canned widget to show these prices, I don't think so since some of the sample sites using the template widget had pricing.
- Some of the sample sites for the Template Widget were buggy.
- This site is interesting - https://www.faribaultmill.com/apps/pulse-personalizer/?variantId=12983339876461&handle=ashby-twill-throw-heathercharcoal&quantity=1&returnurl=https%3A%2F%2Fwww.faribaultmill.com%2Fcollections%2Fwool-throws%2Fproducts%2Fashby-twill-throw-heathercharcoal&sku=BTATRD1475
	- They do have real time pricing
		- 1 line - $20
		- 2 line - $25
		- 3 line - $30
		- Monogram - $20 (these are templates/styles)
- This site has very tight templates where only 2 colors and any template selected has tight controls on what text can be entered and has pricing.
	- https://www.teddypost.se/produkt/bla-kanin-med-namn-bluey/?personalize&variantid=HQ-BBU3&productId=23891&quantity=1&returnUrl=https%3A%2F%2Fwww.teddypost.se%2Fprodukt%2Fbla-kanin-med-namn-bluey%2F
- So the template widget appears you can include the price depending on the widget.
- The big plus for a custom approach to using the UI is the ability to upload a custom logo. So I can't control enabling/disabling the widget.
- Make sure when going to a product-detail page for a golf bag you replace the domain in the url with `http://localhost:3000/`. It currently goes to `rockbottomgolf.com`. This appears to only work from the Rock Bottom Demo Local store. Does not work from Rock Bottom Golf store. I get a 404 not found when going to a product-details page.
- Probably will need to do as Kevin was doing and comment/uncomment the page in the them directly on the demo site and can't test with a local running stencil.
- The "CUSTOMIZE ME" button currently is and add to cart when the widget code is disabled.
- The widget is in `head-scripts-development.html` for Rock Bottom Golf and in `base.html` for Rock Bottom Golf Demo
- figure out how to get demo site working with the widget. I know Kevin mentioned a sandbox area with PulseID.
- `http://localhost:3000/bags-carts/cart-bags/titleist-golf-cart-15-bag/`
- `http://www.pulseidwebapi.com/1/render/Lettering?Text=My text&Font=Block%20New&palette[0]=ff4f88&palette[1]=000ff0`
- `https://rockbottom.pulseidconnect.com/1/render/Lettering?Text=My text&Font=Block%20New&palette[0]=ff4f88&palette[1]=000ff0`
- `https://rockbottom.pulseidconnect.com/1/render/Lettering?Text=My Logo&Font=Block%20New&palette[0]=ff0000`
- `https://rockbottom.pulseidconnect.com/1/render/Lettering?Text=My Logo&Font=Block%20New&palette[0]=ff0000`
- There are 3 widgets here
	- The Freeform Designer
	- The Template Designer
	- The imageRenderer that was the open source stuff that I was trying.
	- We are currently using a custom widget for us that works with BigCommerce called `widgetbcrockbottomff`. This is a custom version of the Freeform Designer.
	- It sound like they are creating a new custom widget for the Template Designer that will probably be named `widgetbcrockbottomtd`
	- They are currently having issues with it.
	- StitchEngine or routing config is blocking public access
	- What You CAN Do Yourself in BigCommerce
		- You can absolutely build a CustomLids-style front-end experience using:
			•	🧩 BigCommerce Stencil or custom checkout
			•	⚙️ JavaScript/React/Vue or plain HTML/CSS
			•	🌐 REST API calls to PulseID
		- You can handle:
			• Custom UI for text/logo input and positioning
			• Font pickers, color selectors, curved/baseline options
			• Preview rendering (with base64 or image URLs)
			• Upload fields (for customer logos)
			• Injecting designId or metadata into the cart or product
			• Order summary preview (e.g. “Customer uploaded logo with red text”)
		- ✅ This is exactly what CustomLids did — they didn’t use the stock PulseID widget on the frontend.
- We will ned API Access from PulseID if we want to pursue a custom UI/Widget approach that we develop in house. 
	- What would this buy us over the canned template designer?
	- Also for the current use of the Freeform designer I can't reference or work with locally. I am getting the following error:
		- `The host in the Tajima Software BigCommerce app does not match the expected host for connecting to PulseID. Please contact Tajima Software support. acsb: This website is not registered or its license is expired.`
		- I may have to request that that PulseID whitelists `http://localhost:3000` or use a tunneling option for a testing URL and have them whitelist this url. You can use a tunneling tool like [ngrok](https://ngrok.com/) or [Cloudflare Tunnel](https://developers.cloudflare.com/cloudflare-one/connections/connect-apps/) to simulate a live domain
- I am receiving the following error when trying to access PulseID
  ```shell
  Access to XMLHttpRequest at 'https://stagerockbottom.pulseidconnect.com/api/api/Designer/GetProduct?variantId=02BBYCHILCT11111111BBS01&originalSize=true&showBackgroundOnZoom=true&sku=02BBYCHILCT11111111BBS01&shop=localhost&shopName=localhost' from origin 'http://localhost:3000' has been blocked by CORS policy: No 'Access-Control-Allow-Origin' header is present on the requested resource.
```

- Solution:
	- Use a Domain Registered with PulseID Instead of localhost. PulseID likely whitelists specific shop domains (like rockbottomgolf.com or demo.rockbottomgolf.com). Using localhost won’t work out of the box.
	- Ask PulseID to Temporarily Whitelist `http://localhost:3000`
	- If you’re actively developing, you can request PulseID support to **add http://localhost:3000 to their allowed origins** on the staging environment. This is often done during testing or widget integration. This would be for `https://stagerockbottom.pulseidconnect.com`
	- Use a Reverse Proxy as a Temporary Workaround (DEV ONLY)
		- You can route API calls through your local dev server, which **avoids the CORS restriction** (not recommended for production):
		- In `stencil.conf.js`, add a proxy:
		  ```javascript
module.exports = {
  // ...
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

- Notes:
	- Then change your API calls to:  `http://localhost:3000/pulseid/api/api/Designer/GetProduct...`
	- **This is only a development workaround.** Do not use this method in production.
	- Make sure the API calls from the browser point to /pulseid/..., not the full external URL.
- To verify if a product is flagged for customizations 
	- Open product in admin console
	- Select Customizations on the left side
		- Should list the following Modifier Options:
			- PulsePersonalize	Text Field
- New template designer is similar to Callaway but have to scroll on a mobile. Try Callaway site on mobile to see if their custom widget (if custom) solves this and use this as a model.
- Look into how we could control the pricing to be similar to he current freeform designer.
- custom lids never scroll. The hat is always present with the design. They are complete freeform.
- Gerber Childrenswear all on one page. But you do have to scroll on mobile
- Emma & Brody is a bigcommerce site which use pulseID.


## Render using a Post

If I start to have issues with the length of the `/Orders/Render` I may want to switch to the Post `i/api/Designer/RenderTemplate/`

![[Pasted image 20250815180615.png]]