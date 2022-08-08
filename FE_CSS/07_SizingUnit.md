# Sizing Units





`ch` unit: 可以帮助用户limit文字的宽度

> Line-height: sets the height of a line box. It is commonly used to set set the distance between lines of texts. 
>
> - On block-level elements, It specifies the minimum 
> - On non-replaced inline element, it specifies the height that is used to calculate line box height

**Numbers**: 数字用来定义 `opacity`, `line-height`. Numbers are unitless integers and decimals.

​	Numbers can also be used in the following places:

		- Setting values for filters: `filter: sepia(0.5)` applies a `50%` sepia filter to the element
		- Setting opacity
		- Color channels
		- transform an element



**Percentages**: 

`width` is calculated as a percentage of the available width in the parent element.

If you set `margin` or `padding` as a percentage, they will be a portion of the **parent element's width**, regardless of direction.



The transform property allows you alter an element's appearance and position by rotating, skewing, scaling and translating it. This can be done in a 2D and 3D space.



##### Dimensions and Lengths

If you attach a unit to a number, it becomes a dimension.

​	For example, `1rem` is a dimension. In this context, the unit that is attached to a number is referred to in specifications as a dimension token. Lengths are **dimensions that refer to distance** and they can either be absolute or relative.



**Absolute lengths**: All absolute lengths resolve against the same base, making them predictable wherever they're used in your CSS.

| Unit                                         | Name                | Equivalent to       |
| :------------------------------------------- | :------------------ | :------------------ |
| [cm](https://www.w3.org/TR/css-values-4/#cm) | Centimeters         | 1cm = 96px/2.54     |
| [mm](https://www.w3.org/TR/css-values-4/#mm) | Millimeters         | 1mm = 1/10th of 1cm |
| [Q](https://www.w3.org/TR/css-values-4/#q)   | Quarter-millimeters | 1Q = 1/40th of 1cm  |
| [in](https://www.w3.org/TR/css-values-4/#in) | Inches              | 1in = 2.54cm = 96px |
| [pc](https://www.w3.org/TR/css-values-4/#pc) | Picas               | 1pc = 1/6th of 1in  |
| [pt](https://www.w3.org/TR/css-values-4/#pt) | Points              | 1pt = 1/72th of 1in |
| [px](https://www.w3.org/TR/css-values-4/#px) | Pixels              | 1px = 1/96th of 1in |



**Relative Lengths**: A relative length is calculated against a base value, much like a percentage. The difference between these and percentages is that you can contextually size elements. This means that CSS has units such as `ch` that use the text size as a basis, and `vw` which is based on the width of the viewport (your browser window). Relative lengths are particularly useful on the web due to its responsive nature.

- Font-size-relative units:

  | unit                                           | relative to:                                                 |
  | :--------------------------------------------- | :----------------------------------------------------------- |
  | [em](https://www.w3.org/TR/css-values-4/#em)   | Relative to the font size, i.e. 1.5em will be 50% larger than the base computed font size of its parent. (Historically, the height of the capital letter "M"). |
  | [ex](https://www.w3.org/TR/css-values-4/#ex)   | Heuristic to determine whether to use the x-height, a letter "x", or `.5em` in the current computed font size of the element. |
  | [cap](https://www.w3.org/TR/css-values-4/#cap) | Height of the capital letters in the current computed font size of the element. |
  | [ch](https://www.w3.org/TR/css-values-4/#ch)   | Average [character advance](https://www.w3.org/TR/css-values-4/#length-advance-measure) of a narrow glyph in the element's font (represented by the "0" glyph). |
  | [ic](https://www.w3.org/TR/css-values-4/#ic)   | Average [character advance](https://www.w3.org/TR/css-values-4/#length-advance-measure) of a full width glyph in the element's font, as represented by the "水" (CJK water ideograph, U+6C34) glyph. |
  | [rem](https://www.w3.org/TR/css-values-4/#rem) | Font size of the root element (default is 16px).             |
  | [lh](https://www.w3.org/TR/css-values-4/#lh)   | Line height of the element.                                  |
  | [rlh](https://www.w3.org/TR/css-values-4/#rlh) | Line height of the root element.                             |

- Viewport-relative units

  You can use the dimensions of the viewport (browser window) as a relative basis. These units portion up the available viewport space.

  | unit                                             | relative to                                                  |
  | :----------------------------------------------- | :----------------------------------------------------------- |
  | [vw](https://www.w3.org/TR/css-values-4/#vw)     | 1% of viewport's width. People use this unit to do cool font tricks, like resizing a header font based on the width of the page so as the user resizes, the font will also resize. |
  | [vh](https://www.w3.org/TR/css-values-4/#vh)     | 1% of viewport's height. You can use this to arrange items in a UI, if you have a footer toolbar for example. |
  | [vi](https://www.w3.org/TR/css-values-4/#vi)     | 1% of viewport's size in the root element's [inline axis](https://www.w3.org/TR/css-writing-modes-4/#inline-axis). Axis refers to writing modes. In horizontal writing modes like English, the inline axis is horizontal. In vertical writing modes like some Japanese typefaces, the inline axis runs top to bottom. |
  | [vb](https://www.w3.org/TR/css-values-4/#vb)     | 1% of viewport's size in the root element's [block axis](https://www.w3.org/TR/css-writing-modes-4/#block-axis). For the block axis, this would be the directionality of the language. LTR languages like English would have a vertical block axis, since English language readers parse the page from top to bottom. A vertical writing mode has a horizontal block axis. |
  | [vmin](https://www.w3.org/TR/css-values-4/#vmin) | 1% of the viewport's smaller dimension.                      |
  | [vmax](https://www.w3.org/TR/css-values-4/#vmax) | 1% of the viewport's larger dimension.                       |



By sizing text with relative units like `em` or `rem`, rather than an absolute unit, like `px`, the size of your text can respond to user preferences. This can include the system font size or parent element's font size, such as the `<body>`. The base size of the `em` is the element's parent and the base size of the `rem` is the base font size of the document. If you don't define a `font-size` on your `html` element, this user-preferred system font size will be honoured if you use relative lengths, such as `em` and `rem`. If you use `px` units for sizing text, this preference will be ignored.



**Miscellaneous Units**:



**Angle units**: In the [color module](https://web.dev/learn/css/color/), we looked at **angle units**, which are helpful for defining degree values, such as the hue in `hsl`. They are also useful for rotating elements within transform functions.



**Resolution units**: In the previous example the value of `min-resolution` is `192dpi`. The `dpi` unit stands for **dots per inch**. A useful context for this is detecting very high resolution screens, such as Retina displays in a media query and serving up a higher resolution image.













