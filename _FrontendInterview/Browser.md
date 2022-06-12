## Browser



### Animations



##### Avoid animating expensive properties

Some properties are more expensive to change than others, and are therefore more likely to make things stutter. For example, 

- `box-shadow` of an element requires a much more expensive paint operation than changing
- changing the `width` of an element is likely to be more expensive than chaning its `transform`



There are two primary ways to create animations on the web: With CSS and With JavaScript. 

​	CSS animations for simpler "one-shot" transitions, like toggling UI element states

​	JavaScript animations when you want to have advanced effects like **bouncing, stop, pause, rewind or slow down**

- Use CSS when you have smaller, self-contained states for UI elements. CSS transitions and animations are ideal for bringing a naviagtion menu in from the side, or showing a tooltip
- Use JavaScript when you need significant control over your animations. The Web Animations API is the standards-based approach, available today in most modern browsers. This provides real objects, ideal for complex object-oriented applications. JS is also useful when you need to stop, pause, slow down or reverse your animations
- Use `requestAnimationFrame` directly when you want to orchestrate an entire scene by hand. It will be useful if you are building a game or drawing to an HTML canvas



**Animate W. CSS**

Specify what you'd like to happen

CSS transitions: 

​	JavaScript can use the `transitioned` event to listen.



CSS animations: which allow you to have much more control over individual animation keyframes, durations and iterations. For example, animate without any user interactions like clicking and with infinite repetitions.



**Animate W. JavaScript and the Web Animations API**

You can use the *Web Animation API* to either animate specific CSS properties or build composable effect objects.

JavaScript animations are *impreative*, You can also encapsualate them inside other objects.

By default, Web Animations only modify the presentation of an element. If you would like to have your object remain at the location it has moved to, then you should modify its underlying styles when the animation has finished.

With JavaScript, you have the total control of element's styles at every step.



##### The Basics of Easing : `https://developers.google.com/web/fundamentals/design-and-ux/animations/the-basics-of-easing`

`slow in` & `ease in`: motion that starts slowly and accelerates

`slow out` & `ease out`: starts quickly and decelerates

**Easing Keywords**:

Keywords that can be used in CSS:

- linear : animations without any kind of easing

  - ```css
    
    transition: transform 500ms linear
    
    ```

- ease-in : start slowly and end fast 

  - ```css
    transition: transform 500ms ease-in;
    ```

    

- ease-out : start more quickly than linear and it also has deceleration at the end

  ```css
  transition: transform 500ms ease-out;
  ```

  

- ease-in-out:

  - ```css
    transition: transform 500ms ease-in-out;
    
    ```

    

##### Custom of easing

**With CSS**: you can define cubic `Bezier curves` to define the timing. 

X axis is Time and Y axis is Value

​	`Bezier Curves`: takes four values or two pairs of numbers: With each pair describing the X and Y coordinates of a cubic Bezier curve's control points. The starting point of the Bezier curve has coordinates (0, 0) and the ending point has coordinates (1,1); you get to set the X and Y values of two control points. The X values for the two control points must be between 0 and 1, and each control point's Y value can exceed the [0, 1] limit

`transition: transform 500ms cubic-bezier(0.465, 0.183, 0.153, 0.946);`



**With JavaScript**:

Sometimes you need even more control than a cubic Bézier curve can provide. If you wanted an elastic bounce feel, you might consider using a JavaScript framework, because this is a difficult effect to achieve with either CSS or Web Animations.

```
Sometimes you need even more control than a cubic Bézier curve can provide. If you wanted an elastic bounce feel, you might consider using a JavaScript framework, because this is a difficult effect to achieve with either CSS or Web Animations.
```





##### Animating Between Views

- Use translations to move between views; avoid using `left`, `top`, or any other property that triggers layout.
- Ensure that any animations you use are snappy and the durations are kept short.
- Consider how your animations and layouts change as the screen sizes go up; what works for a smaller screen may look odd when used in a desktop context.

Transition look and behave like depends on the type of views you are dealing with. 

​	For example: Animating a modal overlay on top of a view should be a different experience from tranistioning between a list and details view.

```
Try to maintain 60fps for all of your animations. That way, your users won't see stuttering animations that interfere with their experience. Ensure that any animating element has will-change set for anything you plan to change well ahead of the animation starting. For view transitions, it’s highly likely you will want to use will-change: transform.
```



**Use transitions to move between views**:

​	Descriptions: Assume that there are two views: a list view and a detail view. As the user taps a list item inside the list view, the details view slides in, and the list view slides out.

​	To achieve this effect: you need a container for both views that has `overflow: hidden` set on it. The two views can both be inside the container side-by-side without showing any horizontal scrollbar;



### Responsive Web Design



**Meet the media query**:

A **media query** allows us to target not only certain device classes, but to actually insepect the physical characteristics of the device rendering our work. 

can used with import `@import url("shetland.css") screen and (max-device-width: 480px);`





## Performance



**Core Web Vitals**:



*Loading (LCP: largest contentful paint)* : measures *loading* performance. To provide a good user experience, LCP should occur within **2.5 seconds** of when the page first starts loading.

*Interactivity (FID: First Input Delay)*: measures *interactivity*. To provide a good user experience, pages should have a FID of **100 milliseconds** or less.

*Visual Stability (CLS: Cumulative Layout Shift)*: measures *visual stability*. To provide a good user experience, pages should maintain a CLS of **0.1.** or less.







##### Loading Performance:





##### Rendering Performace





