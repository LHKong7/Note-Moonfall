# Inheritance



**Inheritance Flow**:

Inheriatnce only cascades downwards



> Not all CSS properties are inheritable, but there are a lot that are. 

```
azimuth
border-collapse
border-spacing
caption-side
color
cursor
direction
empty-cells
font-family
font-size
font-style
font-variant
font-weight
font
letter-spacing
line-height
list-style-image
list-style-position
list-style-type
list-style
orphans
quotes
text-align
text-indent
text-transform
visibility
white-space
widows
word-spacing
```



Every HTML element has every CSS property defined by default with an initial value. An initial value is a property that's not inherited and shows up as a default if the cascade fails to calculate a value for that element.



**How to explicitly inherit and control inheritance**:

Inheritance can affect elements in unexpected ways so CSS has tools to help with that.

**inherit** keyword: You can make any property inherit its parent's computed value with the `inherit` keyword. A useful way to use this keyword is to create exceptions.

**initial** keyword: The `initial` keyword sets a property back to that initial, default value.

**unset** keyword: The `unset` property behaves differently if a property is inheritable or not. If a property is inheritable, the `unset` keyword will be the same as `inherit`. If the property is not inheritable, the `unset` keyword is equal to `initial`.

```css
/* Global color styles for paragraph in authored CSS */
p {
  margin-top: 2em;
  color: goldenrod;
}

/* The p needs to be reset in asides, so you can use unset */
aside p {
  margin: unset;
  color: unset;
}

/* the margin is removed and color reverts back to being the inherited computed value. */
```











