# Box Model



> Everything displayed by CSS is a box. Whether that's a box that uses `border-radius` to look like a circle, or just some text



**Content & Sizing**:

- Extrinsic sizing: 
- Intrinsic sizing: 

`min-content` : tells the box to only be as wide as the intrinsic minimum width of its content

When content is too big for the box it is in, we call this overflow. You can manage how an element handles overflow content, using the `overflow` property.



Boxes are made up of distinct box model areas :

- Margin box: space around the box, defined by `margin` rule on your box. Properties such as `outline` and `box-shadow` occupy this sapce too because they are painted on top, so they donot affect the size of box.
- Border box: surrounds the padding box and its space is occupied by the `border` value. The border box is the bounds of your box and the `border edge` is the limit of what you can visually see.
- Padding box: surrounds the content box and is the sapce created by `padding` property. Because padding is inside the box, the background of the box will be visible in the space that it creates. If our box has overflow rules set, such as `overflow: auto` or `overflow: scroll`, the scrollbars will occupy this space too.
- Content box: area that the content lives in. this content can controil the size of its parent, so is usually the most variably sized area

The default box sizing is ***content-box***, which means padding and borders are added to the overall box.

This alternative box model tells CSS to apply the `width` to the border box instead of the content box. This means that our `border` and `padding` get *pushed in*, and as a result, when you set `.my-box` to be `200px` wide: it actually renders at `200px` wide.

