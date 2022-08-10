# Grid



Grid is useful at combining the control that extrinsic sizing provides with the flexibility of intrinsic sizing, which makes it ideal for this sort of layout.

Grid创造是为了 two-dimensional content -> 同时布局 rows和 columns



**Grid terminology**:

- Grid lines: Gird是由lines创造而成 which run horizontally and vertically。 
  - Lines are numbered starting from 1, with the numbering following the writing mode and script direction of the component
- Grid tracks: 两个Grid line之间的空间。 A row track is between two row lines and a column track between two column lines. When we create our grid we create these tracks by assigning a size to them.
- Grid Cell: the smallest space on a grid defined by the intersection of row and column tracks.
- Grid area: several grid cells together. Grid areas are created by causing an item to span over multiple tracks.
- Gaps: A gutter or alley between tracks. For sizing purposes these act like a regular track. You can't place content into a gap but you can span grid items across it.
- Grid container: The HTML element which has `display: grid` applied, and therefore creates a new grid formatting context for the direct children
- Grid item: 
- A grid item is an item which is a direct child of the grid container.





**Rows & Columns**:

define a grid with three column tracks, two row tracks and a 10 pixel gap between the tracks as follows:

```css
.container {
    display: grid;
    grid-template-columns: 5em 100px 30%;
    grid-template-rows: 200px auto;
    gap: 10px;
}
```

It has three column tracks. Each track uses a different length unit. It has two row tracks, one using a length unit and the other auto.



**Intrinsic sizing keywords**: Grid tracks can use intrinsic sizing keywords. These keywords are defined in the Box Sizing specification and add additional methods of sizing boxes in CSS, not just grid tracks.

- `min-content` : will make a track as small as it can be without the track content overflowing.
- `max-content` : has the opposite effect. The track will become as wide enough for all of the content to display in one long unbroken string. This might cause overflows as the string will not wrap.
- `fit-content()`



**The fr unit**: a flexible length which describes a share of the available space in the grid container. The `fr` unit works in a similar way to using `flex: auto` in flexbox. It distributes space after the items have been laid out.



**minmax() function:**  you can set a minimum and a maximum size for a track. 



**repeat() **: can be used to repeat any section of your track listing. For example you can repeat a pattern of tracks. You can also have some regular tracks and a repeating section.



**auto-fill and auto-fit**: 



##### Auto-placement



**Placing items in columns**: The default behavior of grid layout is to place items along the rows. You can instead cause the items to place into columns using `grid-auto-flow: column`.



**Spanning tracks**: You can cause some or all of the items in an auto-placed layout to span more than one track. Use the `span` keyword plus the number of lines to span as a value for `grid-column-end` or `grid-row-end`.



**Filling gaps**: 

An auto-placed layout with some items spanning multiple tracks may result in a grid with some unfilled cells. The default behavior of grid layout with a fully auto-placed layout is to always progress forward. The items will be placed according to the order they are in the source or any modification with the `order` property. If there is not enough space to fit an item, grid will leave a gap and move to the next track.



By using `grid-auto-flow` with a value of `dense` , grid will take items later in the layout and use them to fill gaps. This may mean that the display becomes disconnected from the logical order.



**Placing items**:

Grid Layout is based on a grid of numbered lines. The simplest way to place things onto the grid is to place them from one line to another, 

The properties that you can use to place items by line number are:

- `grid-column-start`
- `grid-column-end`
- `grid-row-start`
- `grid-row-end`

Shorthands which allow user to set both start and end lines at once:

- `grid-column`
- `grid-row`



**Stacking items**:





**Alignment**:

The properties which begin with `align-` are used on the block axis, the direction in which blocks are laid out in your writing mode.

- [`justify-content`](https://developer.mozilla.org/docs/Web/CSS/justify-content) and [`align-content`](https://developer.mozilla.org/docs/Web/CSS/align-content): distribute additional space in the grid container around or between tracks.
- [`justify-self`](https://developer.mozilla.org/docs/Web/CSS/justify-self) and [`align-self`](https://developer.mozilla.org/docs/Web/CSS/align-self): are applied to a grid item to move it around inside the grid area it is placed in.
- [`justify-items`](https://developer.mozilla.org/docs/Web/CSS/justify-items) and [`align-items`](https://developer.mozilla.org/docs/Web/CSS/align-items): are applied to the grid container to set all of the `justify-self` properties on the items.









