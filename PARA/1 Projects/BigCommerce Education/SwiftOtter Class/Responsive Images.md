- A **responsive image** is an image that automatically **adjusts its size, resolution, or source** based on the user’s device, screen size, or resolution (like Retina displays). The goal is to **optimize performance and display quality** across all devices — desktops, tablets, phones, etc.
- Common Techniques
	- srcset and sizes - Tell the browser to choose the right image version based on screen size and resolution.
	  ```html
	  <img 
  src="image-800.jpg"
  srcset="image-400.jpg 400w, image-800.jpg 800w, image-1600.jpg 1600w"
  sizes="(max-width: 600px) 400px, (max-width: 1200px) 800px, 1600px"
  alt="Example" />
```

- Tell the browser to choose the right image version based on screen size and resolution.
- The **lazysizes** library is a **high-performance JavaScript lazy loader** that helps **defer loading of images (and other media like iframes)** until they enter the viewport. It also supports **responsive images** via srcset and sizes.
- The CornerStone html file that handles this is `responsive-img.html`
- **LQIP** stands for **Low-Quality Image Placeholder**. It’s a **performance optimization technique** used in web development to improve the perceived loading speed of images on a page.