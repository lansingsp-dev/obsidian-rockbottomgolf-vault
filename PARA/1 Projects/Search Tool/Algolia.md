
- Relevant  BigCommerce them files from RBG Demo
	- Important to note that I could not get the Algolia InstanSearch to working locally on my Stencil CLI. But, I did get the Autocomplete to work locally.
	- header-2.html - This includes the quick-search.html. The name parameter is what is referenced in the Algolia configuration for the DESKTOP CSS SELECTOR ** Under the Search Settings
	  
```html
 <div class="dropdown dropdown--quickSearch header-2__nav-search"  data-prevent-quick-search-close>  
    {{> components/common/quick-search name='nav-quick-search' custom_class='nxt-searchbox1'}}  
</div>
```

![[Pasted image 20250814074650.png]]

Page URL - /search-results
Placement Region: page_builder_content

## Algolia Search Setting

Original InstantSearch values

![[Pasted image 20250815095700.png]]

![[Pasted image 20250815113210.png]]

New Settings:

![[Pasted image 20250815160739.png]]

- Steps taken go get search to work
	- Went to Storefront -> Web Pages and made "Search Results" visible.
	- ~~When I opened the /search-results page I replace the warning with:~~
		- ~~For the Page Type, select "Contain raw HTML entered in the text area below"~~
		- ~~Original Page Content - `<!-- WARNING: Modifying this file directly will cause it to be out of sync with Algolia -->`~~
		- ~~I replace it with `<div id="algolia-instantsearch"></div>`~~

## Code Changes
- Comment out Nextopia in `templates/components/custom/scripts/head-scripts.html`
```html
<!-- Nextopia Start -->  
<!--<script type="text/javascript" src="//cdn.nextopia.net/nxt-app/842fa65b7310e3f875729674bd619bcd.js" async defer></script>-->  
<!-- Nextopia End -->
```

- Catch the DY error we were getting in`assets/js/theme/global/quick-search.js`. Note that i did not make this change.  Your are not allow to modify this script live on BigCommerce. See below my changes for `quick-search.html`
```javascript
// Dynamic Yield Event Start  
try {  
    DY.API("event", {  
        name: "Keyword Search",  
        properties: {  
            dyType: "keyword-search-v1",  
            keywords: searchQuery  
        }  
    });  
} catch (error) {  
    console.error("Dynamic Yield event error:", error);  
}  
console.log("Dynamic Yield Search Event");
```

- Update the form in `templates/components/common/quick-search.html` so that data-url is not using ` /search.php` and override the code above to avoid the exception when referencing DY.API. This was added after the form - `data-quick-search-form`

```javascript

<script>  
    (function () {  
        var SELECTOR_FORM = 'form[data-quick-search-form]';  
        var SELECTOR_INPUT = '[data-search-quick]';  
        var DEST_FALLBACK = '/search-results';  
  
        function bindForm(form) {  
            if (!form || form.dataset.algoliaBound) return;  
            form.dataset.algoliaBound = '1';  
  
            if ((form.getAttribute('data-url') || '').trim() === '' ||  
                    form.getAttribute('data-url') === '/search.php') {  
                form.setAttribute('data-url', DEST_FALLBACK);  
            }  
  
            var input = form.querySelector(SELECTOR_INPUT);  
  
            form.addEventListener('submit', function (e) {  
                e.preventDefault();  
                e.stopPropagation();  
                if (typeof e.stopImmediatePropagation === 'function') e.stopImmediatePropagation();  
  
                var q = (input && input.value || '').trim();  
                if (!q) return;  
  
                try {  
                    if (window.DY && typeof DY.API === 'function') {  
                        DY.API('event', {  
                            name: 'Keyword Search',  
                            properties: { dyType: 'keyword-search-v1', keywords: q }  
                        });  
                    }  
                } catch (err) {  
                    console.warn('Dynamic Yield event error:', err);  
                }  
  
                var base = form.getAttribute('data-url') || DEST_FALLBACK;  
                var dest = base + '?search_query=' + encodeURIComponent(q);  
                window.location.assign(dest);  
            }, true);  
  
            if (input) {  
                input.addEventListener('keydown', function (e) {  
                    if (e.key === 'Enter') e.stopPropagation();  
                }, true);  
            }  
        }  
  
        function init() {  
            document.querySelectorAll(SELECTOR_FORM).forEach(bindForm);  
        }  
  
        document.addEventListener('DOMContentLoaded', init);  
        document.addEventListener('stencil:reinitialize', init);  
    })();  
</script>

```