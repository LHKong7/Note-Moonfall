# Pseudo Elements

A pseudo-element is like adding or targeting an extra element without having to add more HTML.



`::first-letter`: to achieve drop cap 



`::before && ::after` : Both the before and after pseudo-elements create a child element inside an element only if you define a `content` property

Content can be any string -- even empty -- anything other than an empty string will likely announced by a screen reader. Image `url` can be inserted as its original dimensions, so you won't be able to resize it.



Once `::before` and `::after` element has been created, you can style it howeveer you want with no limits.You can only insert a `::before` or `::after` element to an element that will accept child elements, so elements such as `image, video and input ` will not work



`::first-letter`:  We met this pseudo-element at the start of the lesson. It is worth being aware that not all CSS properties can be used when targeting [`::first-letter`](https://developer.mozilla.org/docs/Web/CSS/::first-letter). The available properties are:

- color
- background properties
- border
- float
- font
- Text properties



`::first-line` :  will let you style the first line of text only if the element with `::first-line` applied has a `display` value of `block`, `inline-block`, `list-item`, `table-caption` or `table-cell`.

Like the `::first-letter` pseudo-element, there's only a subset of CSS properties you can use:

- `color`
- `background` properties
- `font` properties
- `text` properties



`::backdrop`: 



`::marker` :  pseudo-element lets you style the bullet or number for a list item or the arrow of a `<summary>` element.

Only a small subset of CSS properties are supported for `::marker`:

- `color`
- `content`
- `white-space`
- `font` properties
- `animation` and `transition` properties



`::selection`: allows you to style how selected text looks.



`::placeholder`:  allows you to style that text.

The `::placeholder` only supports a subset of CSS rules:

- `color`
- `background` properties
- `font` properties
- `text` properties









 