# Functions

CSS has a range of inbuilt functions.



##### What is CSS functions

A function is a named, self-contained piece of code that completes a specific task. A function is named so you ca call it within your code and you can pass data into the function.

A lot CSS functions are pure functions which means if you pass the same arguments into them, they will always give you the same result back,



##### Functional Selectors

```css
.post :is(h1, h2, h3) {
	line-height: 1.2;
}
```



`:is()` and `:not()`



##### Custom properties and var()

```css
:root {
	--base-color: #ff00ff;
}

.my-element {
	background: var(--base-color);
}
```

A custom property is a variable which allows users to tokenize values in CSS code. [Custom properties are also affected by the cascade](https://piccalil.li/tutorial/getting-started-with-css-custom-properties/) which means they can be contextually manipulated or redefined. A custom property must be prefixed with two dashes (`--`) and are case sensitive.

 [`var()`](https://developer.mozilla.org/docs/Web/CSS/var())  :  function takes one required argument: the custom property that you are trying to return as a value. 



##### Functions that return a value

`attr()` : taking the content of the `<a>` element's `href` attribute and setting it as the `content` of the `::after` pseudo-element. If the value of the `<a>` element's `href` attribute was to change, this would automatically be reflected in this `content` attribute.



`url()` :  takes a **string** URL and is used to load images, fonts and content. If a valid URL isn't passed in or the resource that the URL points to can't be found, nothing will be returned by the `url()` function.



##### Color functions

Some available color functions in CSS are `rgb()`, `rgba()`, `hsl()`, `hsla()`, `hwb()`, `lab()` and `lch()`. All of these have a similar form where configuration arguments are passed in and a color is returned back.





#### Mathematical expressions

**calc()**: takes a single mathematical expression as its param. 



**min() && max()**: 

- `min()` function returns the smallest computed value of the one or more passed arguments
- `max()` function get the largest value of the one or more passed arguments

```css
.my-element {
  width: min(20vw, 30rem);
  height: max(20vh, 20rem);
}
```



**clamp()**: takes three arguments: the minimum size, the ideal size and the maximum



##### Shapes

The [`clip-path`](https://developer.mozilla.org/docs/Web/CSS/clip-path), [`offset-path`](https://developer.mozilla.org/docs/Web/CSS/offset-path) and [`shape-outside`](https://developer.mozilla.org/docs/Web/CSS/shape-outside) CSS properties use shapes to visually clip your box or provide a shape for content to flow around.



Simple shapes: `circle()` , `ellipse()` and `inset()` take configuration arguments to size them. 

More complex shapes: `polygon()` : take comma separated pairs of X and Y axis values to create custom shapes.



#### Transforms

Overview of CSS functions are the transform functions: skew, resize and even change the depth of an element.



##### Rotation

You can rotate an element using the `rotate()` function, which will rotate an element on its center axis: 

- rotateX()
- rotateY()
- rotateZ

rotate an lement on a specific axis instead.

```css
.my-element {
  transform: rotateX(10deg) rotateY(10deg) rotateZ(10deg);
}
```



**rotate3d()**: function takes four arguments. The first 3 arguments are numbers, which define X Y Z coordinates. The fourth argument is the rotation which like the other rotation functions, accepts degrees, angle and turns.



##### Scale

You can change the scaling of an element with `transform` and the [`scale()`](https://developer.mozilla.org/docs/Web/CSS/transform-function/scale()) function. The function accepts one or two numbers as a value which determine a positive or negative scaling.

- scaleX()
- scaleY()
- scaleZ

There is a [`scale3d()`](https://developer.mozilla.org/docs/Web/CSS/transform-function/scale3d()) function. This is similar to `scale()`, but it takes three arguments: the X, Y and Z scale factor.



**Translate**:

The [`translate()`](https://developer.mozilla.org/docs/Web/CSS/transform-function/translate()) functions move an element while it maintains its position in the document flow. They accept length and percentage values as arguments. 

The `translate()` function translates an element along the X axis if one argument is defined, and translates an element along the X and Y axis if both arguments are defined

```css
.my-element {
  transform: translatex(40px) translatey(25px);
}
```



using [`translateX`](https://developer.mozilla.org/docs/Web/CSS/transform-function/translateX()), [`translateY`](https://developer.mozilla.org/docs/Web/CSS/transform-function/translateY()) and [`translateZ`](https://developer.mozilla.org/docs/Web/CSS/transform-function/translateZ()). You can also use [`translate3d`](https://developer.mozilla.org/docs/Web/CSS/transform-function/translate3d()) which allows you to define the X, Y and Z translation in one function.



**Skewing**:  accept angles as arguments.

You can also use [`skewX`](https://developer.mozilla.org/docs/Web/CSS/transform-function/skewX()) and [`skewY`](https://developer.mozilla.org/docs/Web/CSS/transform-function/skewY()) to affect each axis independently.

```css
.my-element {
  transform: skew(10deg);
}
```



**Perspective**: to alter the distance between the user and the Z plane. This gives the feeling of distance and can be used to create a depth of field in your designs.



##### Animation Functions, gradients and filters

CSS also provides functions that help you [animate](https://web.dev/learn/css/animations) elements, apply [gradients](https://web.dev/learn/css/gradients) to them and use graphical [filters](https://web.dev/learn/css/filters) to manipulate how they look. To keep this module as concise as possible, they are covered in the linked modules.



















