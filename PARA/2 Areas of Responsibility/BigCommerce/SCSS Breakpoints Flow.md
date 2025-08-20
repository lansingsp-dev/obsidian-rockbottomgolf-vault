# BigCommerce SCSS Breakpoints Flow (with file references)

## Overview
In BigCommerce Stencil themes, responsive design is handled by the `breakpoint()` mixin.  
When you use:

```scss
@include breakpoint('medium') {
  // styles
}
```

…the keyword `'medium'` is resolved step-by-step through functions, maps, and variables across several SCSS files until it becomes a specific pixel value.

---

## Step-by-Step Resolution

### 1. Your SCSS code
**File:** `_its_header.scss`
```scss
@include breakpoint('medium') { ... }
```
- Calls the `breakpoint()` mixin with the keyword `'medium'`.

---

### 2. `breakpoint()` mixin
**File:** `_toolkit.scss`
```scss
@mixin breakpoint($size) {
    @if type-of($size) == "number" {
        @media (min-width: $size) { @content; }
    }
    @else {
        @media (min-width: screenSize($size)) { @content; }
    }
}
```
- If you pass a number (e.g. `900px`), it uses it directly.  
- If you pass a keyword (e.g. `'medium'`), it calls the **`screenSize()` function**.

---

### 3. `screenSize()` function
**File:** `_screensizes.scss`
```scss
@function screenSize($key) {
    @if map-has-key($screenSizeMap, $key) {
        @return map-get($screenSizeMap, $key);
    }
    @warn "Unknown `#{$key}` in $screenSizeMap.";
    @return null;
}
```
- Looks up the `$key` (`'medium'`) in the `$screenSizeMap`.  
- If found, it returns the value. If not, it warns you.

---

### 4. `$screenSizeMap` map
**File:** `_screensizes.scss`
```scss
$screenSizeMap: (
    xxxlarge: $screen-xxxlarge,
    xxlarge:  $screen-xxlarge,
    xlarge:   $screen-xlarge,
    large:    $screen-large,
    medium:   $screen-medium,
    small:    $screen-small,
    xsmall:   $screen-xsmall,
    xxsmall:  $screen-xxsmall
);
```
- Defines which variable corresponds to which keyword.  
- `'medium'` → `$screen-medium`.

---

### 5. Screen size variables
**File:** `_screensizes.scss`
```scss
$screen-xxxlarge: 1920px !default;
$screen-xxlarge:  1681px !default;
$screen-xlarge:   1441px !default;
$screen-large:    1281px !default;
$screen-medium:   1025px !default;
$screen-small:     769px !default;
$screen-xsmall:    481px !default;
$screen-xxsmall:   320px !default;
```
- Final pixel values used by the map.  
- For `'medium'`, the value is **1025px**.

---

## Final Output
- `@include breakpoint('medium')`  
→ `screenSize('medium')`  
→ `map-get($screenSizeMap, medium)`  
→ `$screen-medium`  
→ **1025px**

Which compiles to:

```css
@media (min-width: 1025px) {
  /* styles */
}
```

---

## Diagram Flow

```plaintext
_its_header.scss
  |
  v
@include breakpoint('medium')
  |
  v
----------------------------
| _toolkit.scss             |
| breakpoint($size) mixin   |
----------------------------
  | keyword? yes
  v
----------------------------
| _screensizes.scss         |
| screenSize($key) function |
----------------------------
  | map lookup
  v
---------------------------------------
| _screensizes.scss                    |
| $screenSizeMap (medium → $screen-medium) |
---------------------------------------
  |
  v
---------------------------------
| _screensizes.scss              |
| $screen-medium: 1025px !default |
---------------------------------
  |
  v
CSS Output:
@media (min-width: 1025px) { ... }
```

---

## Key Notes
- To change `'medium'`, update `$screen-medium` in `_screensizes.scss` or override it in a custom SCSS file loaded after it.  
- If you change SCSS breakpoints, also update `/assets/js/theme/common/media-query-list.js` to keep JS media queries in sync with SCSS.  
- Bootstrap’s `$grid-breakpoints` (`sm`, `md`, `lg`, etc.) found in `_variables.scss` is **separate** and not used by this `breakpoint()` mixin.  
