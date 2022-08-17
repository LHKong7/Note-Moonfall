# Spacing



##### HTML spacing:

​	***HTML elements***:

HTML 提供了一些方法space 元素. The `<br>` and `<hr>` elements 可以让你在block direction to space elements, which if you are in a latin-based language, is top-to-bottom.

如果你使用 `<br>` 元素， 它会创建一个 line-break, just like if you were to press your enter key in a word processor.

如果你使用 `<hr>` 元素, 它会创建一个  horizontal line with space either-side, known as `margin`.



​	***HTML Entity***:

HTML Entity can create space. An HTML entity is a reserved string of characters that are replaced with character entities by the browser. 

- `&nbsp` entity is converted into a non-breaking space character, which provides an inline space



##### Margin

If you want to add space to the outside of an element, You use the `margin` property.

The `margin` property is shorthand for `margin-top, margin-right, margin-bottom, margin-left`, The shorthand applies properties in a particular order: top, right, bottom and left. You can remember these with trouble: TRouBLe.

The `margin` shorthand can also be used with one, two, or three values. Adding a fourth value lets you set each individual side. These are applied as follows:

- One value will be applied to all sides. (`margin: 20px`).
- Two values: the first value will be applied to the top and bottom sides, and the second value will be applied to the left and right sides. (`margin: 20px 40px`)
- Three values: the first value is `top`, the second value is `left` **and** `right`, and the third value is `bottom`. (`margin: 20px 40px 30px`).



You can also use a value of `auto` for margin. For block level elements with a restricted size, an `auto` margin will take up available space in the direction that it is applied to.



Another good example of `auto` margin is a horizontally centered wrapper which has a max width. This sort of wrapper is often used to create a consistent center column on a website. (水平居中)

```css
.wrapper {
	max-width: 400px;
	margin: 0 auto;
}
```



**Negative margin**:

Negative values can also be used for margin. Instead of adding space between adjacent sibling elements, it will reduce space between them. this can result in overlapping element.



**Margin collapse**:

Margin collapse works by selecting the largest value of two adjoining elements with vertical margin set on the adjoining sides. Only block margins collapse, not inline (horizontal) margins. *CSS will take the larger of the margin spaces between elements yep!*

Two Good Things about margin collapse:

1. Collapsing margins help to set consistent spacing between elements without accidentally creating huge gaps between elements that also have margin defined.
2. Margin collapse also helps with empty elements. If you have a paragraph that has a top and bottom margin of `20px`, it will only create `20px` of space: not `40px`. If *anything* is added to the inside of this element though, including `padding`, its margin will no longer collapse in itself and will be treated as any box with content.



**防止margin collapse**:

If you make an element absolutely positioned, using `position: absolute`, the margin will no longer collapse. The margin also won't collapse if you use the `float` property, too.

IF  apply flexbox with column direction, the margins are combined, instead of collapsed. This can provide predictability with layout work, which is what flexbox and grid containers are designed for.



##### Padding

The `padding` property creates space on the **inside** of your box instead: like insulation.





##### Positioning

Also covered in the [layout](https://web.dev/learn/css/layout/) module, if you set a value for `position` that is anything other than `static`, you can space elements with the `top`, `right`, `bottom` and `left` properties. There are some differences with how these directional values behave:

- An element with `position: relative` will maintain its place in the document flow, even when you set these values. They will be relative to your element's position too.
- An element with `position: absolute` will base the directional values from the relative parent's position.
- An element with `position: fixed` will base the directional values on the viewport.
- An element with `position: sticky` will only apply the directional values when it is in its docked/stuck state.















