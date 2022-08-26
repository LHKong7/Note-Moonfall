# Borders

A border provides a frame for box model.

border box is the frame of boxes, and `border` properties give a huge array of options to create that frame.

### Border properties

**Style**:

For a border to appear, you have to define the `border-style`

To set border style on each side of your box, you can use:

- `[border-top-style](<https://developer.mozilla.org/docs/Web/CSS/border-top-style>)`
- `[border-right-style](<https://developer.mozilla.org/docs/Web/CSS/border-right-style>)`
- `[border-left-style](<https://developer.mozilla.org/docs/Web/CSS/border-left-style>)`
- `[border-bottom-style](<https://developer.mozilla.org/docs/Web/CSS/border-bottom-style>)` .

**Color**:

You can set color on all sides of the box or on each individual side with `border-color`. By default, it uses the box’s current text color: `currentColor`.

**Width**:

The width of a border is how thick the line is, and is controlled by `[border-width](<https://developer.mozilla.org/docs/Web/CSS/border-width>)`. The default border width is `medium`. This won't be visible unless you define a style, though. You can use other named widths such as `thin` and `thick`.

##### Logical Properties applies to border too



##### Border radius

To give a box rounded corners use the [`border-radius`](https://developer.mozilla.org/docs/Web/CSS/border-radius) property.



You can define these values in the `border-radius` shorthand, using a `/` to define the elliptical values, after the standard values. This enables you to get creative and make some complex shapes.

```
.my-element {
	border: 2px solid;
  border-radius: 95px 155px 148px 103px / 48px 95px 130px 203px;
}
```





##### Border images



