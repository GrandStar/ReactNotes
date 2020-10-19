# GPU Animation



![CSS animation using the transform property looks much smoother than one using the left and top properties. ](../.gitbook/assets/image%20%2868%29.png)

Use `transform: translateZ(0)` or `will-change: transform`

\`\`

* 3D transforms: `translate3d`, `translateZ` and so on;
* `<video>`, `<canvas>` and `<iframe>` elements;
* animation of `transform` and `opacity` via `Element.animate()`;
* animation of `transform` and `opacity` via СSS transitions and animations;
* `position: fixed`;
* [`will-change`](https://www.w3.org/TR/css-will-change-1/);
* [`filter`](https://drafts.fxtf.org/filters/#FilterProperty);



**PROS**

* The animation is fast and smooth, at 60 frames per second.
* A properly crafted animation works in a separate thread and is not blocked by heavy JavaScript calculations.
* 3D transforms are “cheap.”

**CONS**

* Additional repainting is required to promote an element to a composite layer. Sometimes this is very slow \(i.e. when we get a full-layer repaint, instead of an incremental one\).
* Painted layers have to be transferred to the GPU. Depending on the number and size of these layers, the transfer can be very slow, too. This could lead to an element flickering on low-end and mid-market devices.
* Every composite layer consumes additional memory. Memory is a precious resource on mobile devices. Excessive memory use could **crash the browser**.
* If you don’t consider implicit compositing, then the chances of slow repainting, extra memory usage and browser crashes are very high.
* We get visual artifacts, such as with text rendering in Safari, and page content will disappear or get distorted in some cases.



**USE CSS TRANSITIONS AND ANIMATIONS WHENEVER POSSIBLE**

 animation of `transform` and `opacity` via CSS transitions or animations automatically creates a compositing layer and works on the GPU. We could also animate via JavaScript, but we’d have to add `transform: translateZ(0)` or `will-change: transform, opacity` first in order to ensure that the element gets its own compositing layer.





main principles

* Always negotiate with the client and designer about all animations and effects on the website. It could affect the page’s markup greatly and make for better compositing.
* Watch out for the number and size of composite layers from the very beginning — especially ones created by implicit compositing. The “Layers” panel in your browser’s development tools is your best friend.
* Modern browsers make heavy use of compositing not just for animation but to the painting of page elements. For example, `position: fixed` and the `iframe` and `video` elements use compositing.
* The size of compositing layers is likely be more important than the number of layers. In some cases, the browser will try to reduce the number of composite layers \(see the “Layer Squashing” section of “[GPU Accelerated Compositing in Chrome](https://www.chromium.org/developers/design-documents/gpu-accelerated-compositing-in-chrome)”\); this prevents so-called “layer explosion” and reduces memory consumption, especially when layers have large intersections. But sometimes, such optimization has a negative impact, such as when a very large texture consumes much more memory than a few small layers. To bypass this optimization, I add a small, unique `translateZ()` value to each element, such as `translateZ(0.0001px)`, `translateZ(0.0002px)`, etc. The browser will determine that the elements lie on different planes in the 3D space and, thus, skip optimization.
* You can’t just add `transform: translateZ(0)` or `will-change: transform` to any random element to virtually improve animation performance or to get rid of visual artifacts. GPU compositing has many drawbacks and tradeoffs to be considered. When not used sparingly, compositing will decrease overall performance at best, and crash browsers at worst.

