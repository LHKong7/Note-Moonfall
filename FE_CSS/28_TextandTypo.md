# Text && typography



### Change the typeface

`font-family` : to change the typeface of the text.

The `font-family` property accepts a comma-separated list of strings, either referring to *specific* or *generic* font families.



### Use italic and oblique fonts

Use [`font-style`](https://developer.mozilla.org/docs/Web/CSS/font-style) to set whether text should be italic or not. `font-style` accepts one of the following keywords: `normal`, `italic`, and `oblique`.







### Make text bold

`font-weight` to set the "boldness" of text. This property accepts keyword values (normal, bold), relative keyword values (lighter, bolder) and numeric 

### Change the size of text

Use [`font-size`](https://developer.mozilla.org/docs/Web/CSS/font-size) to control the size of your text elements. This property accepts length values, percentages, and a handful of keyword values.

In addition to length and percentage values, `font-size` accepts some *absolute* keyword values (`xx-small`, `x-small`, `small`, `medium`, `large`, `x-large`, `xx-large`) and a couple of *relative* keyword values (`smaller`, `larger`). The relative values are relative to the parent element’s `font-size`.

### Change the space between lines

Use [`line-height`](https://developer.mozilla.org/docs/Web/CSS/line-height) to specify the height of each line in an element. This property accepts either a number, length, percentage, or the keyword `normal`. Generally, it’s recommended to use a number instead of a length or percentage to avoid issues with inheritance.

### Change the space between characters

Use [`letter-spacing`](https://developer.mozilla.org/docs/Web/CSS/letter-spacing) to control the amount of horizontal space between characters in your text. This property accepts length values such as `em`, `px`, and `rem`.



### Change the space between words 

Use [`word-spacing`](https://developer.mozilla.org/docs/Web/CSS/word-spacing) to increase or decrease the length of space between each word in your text. This property accepts length values such as `em`, `px`, and `rem`. Note that the length you specify is for *extra* space in addition to the normal spacing. This means that `word-spacing: 0` is equivalent to `word-spacing: normal`.



### Change the case of text

Use [`text-transform`](https://developer.mozilla.org/docs/Web/CSS/text-transform) to modify the capitalization of your text without needing to change the underlying HTML. This property accepts the following keyword values: `uppercase`, `lowercase`, and `capitalize`.



### Add underlines, overlines, and through-lines to text [#](https://web.dev/learn/css/typography/#add-underlines,-overlines,-and-through-lines-to-text)

The [`text-decoration-line`](https://developer.mozilla.org/docs/Web/CSS/text-decoration-line) property accepts the keywords `underline`, `overline`, and `line-through`. You can also specify multiple keywords for multiple lines.



### Add an indent to your text

Use [`text-indent`](https://developer.mozilla.org/docs/Web/CSS/text-indent) to add an indent to your blocks of text. This property takes either a length (for example, `10px`, `2em`) or a percentage of the containing block’s width.



### Control white-space [#](https://web.dev/learn/css/typography/#control-white-space)

The [`white-space`](https://developer.mozilla.org/docs/Web/CSS/white-space) property is used to specify how whitespace in an element should be handled. For more details, check out the [`white-space` article on MDN](https://developer.mozilla.org/docs/Web/CSS/white-space).



### Control how words break

Use [`word-break`](https://developer.mozilla.org/docs/Web/CSS/word-break) to change how words should be “broken” when they would overflow the line. By default, the browser will not split words. Using the keyword value `break-all` for `word-break` will instruct the browser to break words at individual characters if necessary.



### Change text alignment

Use [`text-align`](https://developer.mozilla.org/docs/Web/CSS/text-align) to specify the horizontal alignment of text in a block or table-cell element. This property accepts the keyword values `left`, `right`, `start`, `end`, `center`, `justify`, and `match-parent`.

### Change the direction of text

Use [`direction`](https://developer.mozilla.org/docs/Web/CSS/direction) to set the direction of your text, either `ltr` (left to right, the default) or `rtl` (right to left). Some languages like Arabic, Hebrew, or Persian are written right to left, so `direction: rtl` should be used. For English and all other left-to-right languages, use `direction: ltr`.

### Change the flow of text [#](https://web.dev/learn/css/typography/#change-the-flow-of-text)

Use [`writing-mode`](https://developer.mozilla.org/docs/Web/CSS/writing-mode) to change the way text flows and is arranged. The default is `horizontal-tb`, but you can also set `writing-mode` to `vertical-lr` or `vertical-rl` for text that you want to flow horizontally.

### Add a shadow to text [#](https://web.dev/learn/css/typography/#add-a-shadow-to-text)

Use [`text-shadow`](https://developer.mozilla.org/docs/Web/CSS/text-shadow) to add a shadow to your text. This property expects three lengths (`x-offset`, `y-offset`, and `blur-radius`) and a color.

### Variable fonts [#](https://web.dev/learn/css/typography/#variable-fonts)

Typically, “normal” fonts require importing different files for different versions of the typeface, e.g. bold, italic, or condensed. Variable fonts are fonts that can contain many different variants of a typeface in one file.





The [`font-variant`](https://developer.mozilla.org/docs/Web/CSS/font-variant) property is a shorthand for a number of CSS properties that let you choose font variants like `small-caps` and `slashed-zero`. The CSS properties this shorthand includes are [`font-variant-alternates`](https://developer.mozilla.org/docs/Web/CSS/font-variant-alternates), [`font-variant-caps`](https://developer.mozilla.org/docs/Web/CSS/font-variant-caps), [`font-variant-east-asian`](https://developer.mozilla.org/docs/Web/CSS/font-variant-east-asian), [`font-variant-ligatures`](https://developer.mozilla.org/docs/Web/CSS/font-variant-ligatures), and [`font-variant-numeric`](https://developer.mozilla.org/docs/Web/CSS/font-variant-numeric). Check out the links on each property for more details about its usage.