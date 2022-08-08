# Flexbox



Flexible Box Layout Model (flexbox) is a layout model designed for one-dimensional content. It excels at taking a bunch of items which have different sizes, and returning the best layout for those items.



Flexbox is the ideal model for this sidebar pattern.



Flexbox not only helps lay the sidebar and content out inline, but where there's not enough space remaining, the sidebar will break onto a new line.



##### What can you do with a flex layout:

- They can display as a *row* or a *column*
- They respect the writing mode of the document.
- They are single line by default, but can be asked to wrap onto multiple lines.
- Items in the layout can be visually reordered, away from their order in the DOM
- Space can be distributed inside the items, so they become bigger and smaller according to the space available in their parent
- Space can be distributed around the items and flex lines in a wrapped layout, using the Box Alignment properties
- The items themselves can be aligned on the cross axis.



**Main Axis & Cross Axis**:



main axis is the one set by `flex-direction` 

- `row` -> main axis is along the row, cross axis is along the column
- `column` -> main axis is along the column, cross axis is along the row

> 所有CSS properties （特性） 有着初始值 which 控制着元素具体怎么表现 "out of the box"当你没有使用任何CSS去改变初始状态。flexbox中的children成为 flex items 只要父元素使用 display：flex， 这些子元素 mean that we start seeing some flexbox ehavior

The initial values means that:

- Items display as a row.
- They do not wrap.
- They do not grow to fill the container.
- They line up at the start of the container.



##### Controlling the direction of items:

`flex-direction` initial value is `row`, If you want a row then you donot need to add the property. To change the direction, add the property and one of the four values:

- `row` : the items lay out as a row
- `row-reverse` : the items lay out as a row from the end of the flex container
- `column` : the items lay out as a column
- `column-reverse` : the items lay out as a column from the end of the flex container

```
You should be cautious when using any properties that reorder the visual display away from how things are ordered in the HTML document, as it can negatively impact accessibility. The `row-reverse` and `column-reverse` values are a good example of this. The reordering only happens for the visual order, not the logical order. This is important to understand as the logical order is the order that a screen reader will read out the content, and anyone navigating using the keyboard will follow.
```

***Writing modes and direction***:

Flex items lay out as a row by default. A row runs in the direction that sentences flow in the writing mode and script direction. In some languages, right-to-left (rtl) script direction, the items will line up on the right. Tab order would also begin on the right as this is the way sentences are read in some language.

If you are working with a vertical writing mode, then a row will run vertically from top to bottom.

main axis: `main-start` and `end-axis`

cross axis:  `cross-start` and `cross-end`

***Wrapping flex items***:

initial value of `flex-wrap` is `no-wrap` . This means that if tehre is not enough space in the container the items will overflow.

Items displaying using the initial values will shrink as small as they can, down to the `min-content` size before overflow happens.

***The flex-flow shorthand***:

`flex-flow` can be used by `flex-direction` and `flex-wrap` properties



##### Controlling space inside flex items:

The initial value of flex item are:

- `flex-grow: 0` items do not grow
- `flex-shrink : 1` items can shrink smaller than their `flex-basis` 
- `flex-basis: auto` items have a base size of `auto`

Using `flex: auto` will mean that items end up different sizes, as the space that is shared between the items is shared out after each item is laid out as max-content size.

To force all of the items to be a consistent size and ignore the size of the content change `flex:auto` to `flex:1` 

This unpacks to:

- `flex-grow: 1` : items can grow larger than their `flex-basis` 
- `flex-shrink: 1`: items can shrink smaller than their `flex-basis` 
- `flex-basis: 0` items have a base size of 0



**Flexbox alignment overview:**

The set of properties can be placed into two groups:

- space distribution:
  - `justify-content` : space distribution on the main axis 
  - `align-content` :  space distribution on the cross axis
  - `place-content`:  a shorthand for setting both of the above properties
- alignment:
  - `align-self` : aligns a single item on the cross axis
  - `align-items`:  aligns all of the items as a group on the cross axis

If you are working:

-  on the main axis then the properties begin with `justify-`. 
-  on the cross axis they begin with `align-`.



##### Dustributing space on the main axis

`justify-content` : the items line up at the start of the flex container.

- flex-start
- flex-end
- center
- space-around
- space-between
- space-evenly

**With flex-direction: column**:

If `flex-direction: column`, `justify-content` will work on the column. To have spare space in the container when working as a column you need to give the container a `height` or `block-size` . Otherwise you won't have spare space to distribute.



##### Distributing space between flex lines

With a wrapped flex container you might have space to distribute on the cross axis. In this case, you can use `align-content` property with the same values as `justify-content` which aligns items to `flex-start` by default, the initial value of `align-content` is `stretch` . 



**The `place-content` shorthand**:

To set both `justify-content` and `align-content` you can use `place-content` with one or two values. A single value will be used for both axes, if you specify both the first is used for `align-content` and the second for `justify-content`.



##### Aligning items on the cross-axis

On the cross-axis you can also align the items within the flex line using `align-items` and `align-self` The space available for this alignment will depend on the height of the flex container or flex line in the case of wrapped set of items.

The initial value of `align-self` is `stretch`, which is why flex items in a row stretch to the height of the tallest item by default.

The `align-self` property is applied to individual items. The `align-items` property can be applied to the flex container to set all of the individual `align-self` properties as a group.

Flex items act as a group on the main axis. So there is no concept of splitting an individual item out of that group.



It is worth knowing that flexbox does work very nicely with auto margins. If you come across a need to split off one item from a group, or separate the group into two groups you can apply a margin to do this.



##### How to center an item vertically and horizontally

The alignment properties can be used to center an item inside another box. The `justify-content` property aligns the item on the main axis, which is row. The `align-items` property on the cross axis.

```css
.container {
  width: 400px;
  height: 300px;
  display: flex;
  justify-content: center;
  align-items: center;
}
```

















































