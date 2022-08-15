# Logical Properties





##### Terminology

The physical proeprties of top, right, bottom and left refer to the physical dimensions of the viewport. 



**Block flow**:

the direction in which content blocks are placed.



**Inline flow**:

 

**Flow relative**:

Historically in CSS, we have only been able to apply properties like margin relative to the direction of their sides.

we have only been able to apply properties like margin relative to the direction of their sides. For example, `margin-top` is applied to the physical top of the element. With logical properties, `margin-top` becomes `margin-block-start`. This means that regardless of language and text direction, the **block flow** has appropriate margin rules.



**Sizing**:

To prevent an element exceeding a certain width or height, write a rule like this:



```css
.my-element {
  max-width: 150px;
  max-height: 100px;
}
```

The flow-relative equivalents are `max-inline-size` and `max-block-size`. You can also use `min-block-size` and `min-inline-size` instead of `min-height` and `min-width`. With logical properties, that max width and height rule would look like this:

```css
.my-element {
  max-inline-size: 150px;
  max-block-size: 100px;
}
```



**start and end**:

Instead of using directions such as top, right, bottom and left, use start and end. This gives you block-start, inline-end, block-end, and inline-start. These allow you to apply CSS properties that respond to writing mode changes.

To align text to the right:

```css
p {
	text-align: right;
}
```



If your aim is not to align to the physical right, but rather to the start of the reading direction, this isn't helpful. With logical values, there are more helpful `start` and `end` values which map to the text direction.

```css
p {
  text-align: end;
}
```



**Spacing and positioning**:

Logical properties for `margin, padding, inset` make positioning elements, and determining how these elements interact with each other across writing modes easier and more efficient.

```css
.my-element {
  padding-top: 2em;
  padding-bottom: 2em;
  margin-left: 2em;
  position: relative;
  top: 0.2em;
}


.my-element {
  padding-block-start: 2em;
  padding-block-end: 2em;
  margin-inline-start: 2em;
  position: relative;
  inset-block-start: 0.2em;
}
```



**Units**

Logical properties bring two new units: `vi` and `vb`. A `vi` unit is 1% of the viewport size in the inline direction. The non-logical property equivalent is `vw`. The `vb` unit is 1% of the viewport in the block direction. The non-logical property equivalent is `vh`.





