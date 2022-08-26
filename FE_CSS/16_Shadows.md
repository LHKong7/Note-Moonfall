# Shadows





CSS has the `box-shadow` and `text-shadow` properties, 

- Box-shadow: the shadow is on the surrounding box
  - `drop-shadow()` : applies a drop shadow effect to the input image.



The order of values for `box-shadow` are as follows:

1. Horizontal offset : a positive number pushes it out from the left and a negative number will push it out from the right
2. Vertical offset
3. Blur radius
4. Spread radius
5. Color



To make a box shadow an inner shadow, rather than the default outer shadow, add an `inset` keyword **before** the other properties.

```css
/* Outer shadow */
.my-element {
	box-shadow: 5px 5px 20px 5px #000;
}

/* Inner shadow */
.my-element {
	box-shadow: inset 5px 5px 20px 5px #000;
}
```



You can add as many shadows as you like with `box-shadow`.

**Properties affecting box-shadow**: Add a `border-radius` to the box will affect the shape of the box shadow. This is because CSS is creating a shadow based on the shape of the box as if light is pointing as it.



If the box with `box-shadow` is in a container that has `overflow: hidden` , the shadow will not break out of that overflow either.





##### Text shadow

The text shadow is similar to box-shadow property. It only works on text nodes.

When you add a `box-shadow`  it is clipped to the shape of the box, but `text-shadow` has no clipping. This means that if the text is fully or semi transparent, the shadow is visible through it.



**Multiple Shadows**:

You can add as many shadows as you like with text-shadow.



##### Drop shadow

Using `drop-shadow` 









