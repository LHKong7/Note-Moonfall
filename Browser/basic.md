##### Rendering pipeline

**sequential** steps:

1. Style: Calculate the styles that apply to the elements
2. Layout : Generate the geometry and position for each element
3. Paint : Fill out the pixels for each element into layers
4. Composite: Draw the layers to the screen

if you animate something that changes layout, the paint and composite steps also have to run again. Animating something that changes layout is therefore more expensive than animating something that only changes compositing.



**Layout changes** involve calculating the geometry (postion and size) of all the elements affected by the change. If changing one element, the geometry of other elements may need to be recalculated. 

​	The larger the tree of visible elements, the longer it takes to perform layout calculations.



**Paint**: the process of determining in what order elements should be paint to the screen. Often the longest-running of all tasks in the pipeline.

​	The majority of painting in modern browsers is done in [software rasterizers](https://software.intel.com/content/www/us/en/develop/articles/software-vs-gpu-rasterization-in-chromium.html). 



**Compositing**: the process of separating the page into layers, converting the information about how the page should look into pixels (rasterization) and putting the layers together to create a page (compositing)

This is why the `opacity` property is included in the list of things which are cheap to animate. ***As long as this property is in its own layer, changes to it can be handled by the GPU during the compositing step.*** Chromium-based browsers and WebKit create a new layer for any element which has a CSS transition or animation on `opacity`.



creating new layers should be done with care because each layer uses memory.  On devices with limited memory creating new layers may cause more of a performance problem than the one you are trying to solve. In addition, each layer's textures need to be uploaded to the GPU. Therefore you may well hit constraints of bandwidth between the CPU and GPU.



Modern browsers can animate two CSS properties cheaply: `transform` and `opacity`. If each frame does not complete within 16.7ms (1000ms / 60 ≈ 16.7), then users will perceive the delay.



CSS-based animations, and [Web Animations](https://web.dev/web-animations/) (in the browsers that support the API), are typically handled on a thread known as the *compositor thread*. This is different from the browser's *main thread*, where styling, layout, painting, and JavaScript are executed. This means that if the browser is running some expensive tasks on the main thread, these animations can keep going without being interrupted. ***As explained in this article, other changes to transforms and opacity can, in many cases, also be handled by the compositor thread.***



**Force layer creation**: you can manually force layer creation with the `will-change` property. this property tells the browser that this element is going to be changed in some way.

```css
// DON'T
.box {
  position: absolute;
  top: 10px;
  left: 10px;
  animation: move 3s ease infinite;
}

@keyframes move {
  50% {
     top: calc(90vh - 160px);
     left: calc(90vw - 200px);
  }
}

// DO:
.box {
  position: absolute;
  top: 10px;
  left: 10px;
  animation: move 3s ease infinite;
}

@keyframes move {
  50% {
     transform: translate(calc(90vw - 200px), calc(90vh - 160px));
  }
}
```



