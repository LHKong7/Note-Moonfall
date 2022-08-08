# Layout



**CSS layout over time:**

- 1996 CSS 1 Floats
- 1998 CSS 2
- 2010 CSS 3 Responsive Web Design
- 2012 Media Queries, Flexbox
- 2017 Grid
- 2019 Intrinsic Web Design
- 2021 Container Queries



##### Display

The `display` property does two things:

- it does is determine if the box it is applied to acts as inline or block
  - inline element: They sit next to each other in the inline direction. 
    - Such as: `<span> or <strong>` : used to sytle pieces of text within containing elements like a `<p>` 
    - Cannot set explicit width and heigt on inline elements. Any block level margin and padding will be ignored by the surrounding elements.
  - Block element: donot sit alongside each other. They create a new line for themselves.
    -  A block element will expand to the size of the inline dimension, therefore spanning the full width in a horizontal writing mode. The margin on all sides of a block element will be respected.
- Determines how an element's children should behave
  - Flexbox: makes the box a block-level box and also converts its children to flex items.



###### Layout Mechanisms



**Flexbox**: one-dimensional layouts. Layout across a single axis, either horizontally or vertically.

- Default: flexbox will align the element's children next to each other, in the inline direction, and stretch them in the block direction, they share the same height.
- Changing behaviour : `align-items`, `justify-content` and `flex-wrap`
- Flexbox also converts the child elements to be **flex items**, which means you can write rules on how they behave inside a flex container. You can change alignment, order and justification on an individual item. How it shrinks or grows using `flex` property
- `flex` : `flex-grow` , `flex-shrink` and `flex-basis` 



**Grid**: control multi-axis layouts. instead of single-axis layouts (vertical or horizontal space).

- 提供 primitives for layout styling: `repeat()` and `minimax()` 

- `fr ` unit: a fraction of remaining space. 

- `grid-row` and `grid-column` properties instruct the first element in the grid to span to the start of the fourth column, from the first column, then span to the third row, from the first row.

  ```
  .my-element :first-child {
    grid-row: 1/3;
    grid-column: 1/4;
  }
  ```

  



Differences: flexbox treats items as a group, grid gives precise control over their placesment in two dimensions.



***Flow Layout***:

If not using grid or flexbox, your elements display in normal flow. There are a number of layout methods that you can use to adjust the behavior and position of items when in normal flow.



**Inline block**: gives you a box that has some of the characteristics of a block-level element, but still flows inline with the text.



**Floats**: The `float` property instructs an element to "float" to the direction specified. When you use `float`, keep in mind that any elements following the floated element may have their layout adjusted. To prevent this, you can clear the float, either by using `clear: both` on an element that follows your floated element *or* with `display: flow-root` on the parent of your floated elements.



**Multicolumn layout**: 

If you have a really long list of elements, such as a list of all of the countries of the world, it can result in *a lot* of scrolling and time wasted for a user. It can also create excess whitespace on the page. With CSS multicolumn, you can split this into multiple columns to help with both of these issues.

```
<h1>All countries</h1>
<ul class="countries">
  <li>Argentina</li>
  <li>Aland Islands</li>
  <li>Albania</li>
  <li>Algeria</li>
  <li>American Samoa</li>
  <li>Andorra</li>
  …
</ul>

.countries {
	column-count: 2;
	column-gap: 1em;
}
```







**Positioning**: The `position` property changes how an element behaves in the normal flow of the document, and how it relates to other elements. The available options are `relative`, `absolute`, `fixed` and `sticky` with the default value being `static`.

`This element is nudged 10px down based on its current position in the document, as it is positioned relative to itself.`



An element with a `position` value of `fixed` behaves in a similar way to `absolute`, with its parent being the root `<html>` element. Fixed position elements stay anchored from the top left based on the `top`, `right`, `bottom` and `left` values that you set.



When you set `position` to `absolute`, it breaks the element out of the current document flow. This means two things:

1. You can position this element wherever you like, using `top`, `right`, `bottom` and `left` in its nearest relative parent.
2. All of the content surrounding an absolute element reflows to fill the remaining space left by that element.

