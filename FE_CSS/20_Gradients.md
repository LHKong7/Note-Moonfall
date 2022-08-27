# Gradients

A gradient is an image and can be used anywhere images can be used, but it is created with CSS and is made up with colors, numbers and angles.



##### Linear Gradient

`linear-gradient` generates an image of two or more colors, progressively. It takes multiple arguments.

- passing an angle or keywords that represent an angle



##### Radial Gradient : radiates in a circular fashion

but instead of specifying an angle, you optionally specify a position and ending shape. If you just specify colors, the `radial-gradient()` will auto-select the position as `center` and select either a circle or ellipse, depending on the size of the box.



The gradient's position is similar to `background-position` using keywords and/or number values. The size of the radial gradient determines the size of the gradient's ending shape (circle or ellipse) and by default will be `farthest-corner`, which means it exactly meets the farthest corner of the box from the center. You can also use the following keywords:

- `closest-corner` will meet the closest corner to the center of the gradient.
- `closest-side` will meet the side of the box closest to the center of the gradient.
- `farthest-side` will do the opposite to `closest-side`.



##### Conic gradient : Good use case for pie charts by CSS

A conic gradient has a center point in the box and starts from the top (default) and goes around in a 360 degree circle.

```
.my-element {
	background: conic-gradient(white, black);
}
```

The [`conic-gradient()`](https://developer.mozilla.org/docs/Web/CSS/conic-gradient()) function accepts position and angle arguments.

By default, the angle is 0 degrees which starts at the top, in the center. If you were to set the angle to be `45deg`, it would be the top right corner. The angle argument accepts any type of angle value, like the linear and radial gradients.



##### Repeating and mixing

Each type of gradient has a repeating type, too. These are [`repeating-linear-gradient()`](https://developer.mozilla.org/docs/Web/CSS/repeating-linear-gradient()), [`repeating-radial-gradient()`](https://developer.mozilla.org/docs/Web/CSS/repeating-radial-gradient()) and [`repeating-conic-gradient()`](https://developer.mozilla.org/docs/Web/CSS/repeating-conic-gradient()). They are similar to the non-repeating functions and take the same arguments. The difference is that if the defined gradient can be repeated to fill the box, based on both of their sizes, it will.