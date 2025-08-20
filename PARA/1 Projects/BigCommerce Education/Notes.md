- Kevin said that Channel Advisor is pushing/syncing the data into the BigCommerce stencil objects.
- All javascript code get compiled into `assets/dist/theme-bundle.*.js`. The entry points for javascript are defined in `webpack.common.js`. Stencil uses webpack for JavaScript bundling, minification and code splitting.
- The product-listing page under categories goes out to the Nextopia/Searchspring and gets dynamicaly updates by this javascript code.
	- head-script.html
	- This line loads an external JavaScript file from the Nextopia CDN. The script likely adds search, merchandising, or recommendation features to the site. The `async` and `defer` attributes ensure the script loads asynchronously and executes after the HTML is parsed, improving page load performance.
	- That is why when I added text to the category.html file it flashed quickly and then go replace with this.
	- In the production site the injection of product-listing.html is actually commented out.
	  ```html
	  <script type="text/javascript" src="//cdn.nextopia.net/nxt-app/842fa65b7310e3f875729674bd619bcd.js" async defer></script>
```


- If you don't see themes under the StoreFront in the BigCommerce admin that mean there are multiple channels/storefronts. You need to navigate to the Channels and the themes will be list under each channel.