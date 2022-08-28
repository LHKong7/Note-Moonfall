# Overflow

*Overflow is how you deal with content that doesn’t fit in a set parent size.*



When content extends beyond its parent, there are many options for how you can handle it. You can scroll to add additional space, clip the overflowing edges, indicate the cut-off with an ellipsis, and so much more. 

***Overflow is especially important to consider when developing for phone applications and multiple screen sizes.***



There are two different clipping options in CSS:

- `text-overflow` will help with individual lines of text
- `overflow` properties will help control overflow in the box model.



##### Single line overflow with text-overflow

`text-overflow` property on any element that contains text node(s). All viewable HTML text on a page is in text nodes. To use `text-overflow`  user need a single unwrapped line of text, user must also set `overflow` to `hidden` and have a `white-space` value that prevents wrapping.

```css
p {
    text-overflow: ellipsis;
    overflow: hidden;
    white-space: nowrap;   
}
```







### Scrolling on the vertical and horizontal axis [#](https://web.dev/learn/css/overflow/#scrolling-on-the-vertical-and-horizontal-axis)

The `overflow-y` property controls physical overflow along the vertical axis of the device viewport, therefore scrolling up and down.

The `overflow-x` property controls overflow along the horizontal axis of the device viewport, therefore scrolling left and right.



The [`overflow-inline`](https://developer.mozilla.org/docs/Web/CSS/overflow-inline) and [`overflow-block`](https://developer.mozilla.org/docs/Web/CSS/overflow-block) properties set the overflow based on the document direction and writing mode.



**overflow shorthand**: The [`overflow`](https://developer.mozilla.org/docs/Web/CSS/overflow) shorthand sets both `overflow-x` and `overflow-y` styles in one line:



##### Scrolling and overflow

It's important to make sure that the scrollable area can accept focus so that a keyboard user can tab to the box, then use the arrow keys to scroll. To allow a scrolling box to accept focus add `tabindex="0"`, a name with the [`aria-labelledby`](https://developer.mozilla.org/docs/Web/Accessibility/ARIA/Attributes/aria-labelledby) attribute, and an appropriate `role` attribute. 



**Scrollbar positioning within box model**:

​	Scroll bars take up space within the padding box and can compete for space if `inline` and not `overlayed`.

**root-scroller vs. implicit-scroller**:

​	To create a root scroller, you can use something called *scroller promotion* by positioning a container as fixed, ensuring it covers the entire viewport and is z-index on top with a scroller.



**scroll-behavior**:

`scroll-behavior` : allows you to opt into browser-controlled scrolling to elements. This allows you to specify how in-page navigation like `.scrollTo()` or links are handled.



This is especially useful when used with [prefers-reduced-motion](https://developer.mozilla.org/docs/Web/CSS/@media/prefers-reduced-motion) to specify scroll behavior based on user preference.

```css
@media (prefers-reduced-motion: no-preference) {
  .scroll-view {
    scroll-behavior: auto;
  }
}
```



**overscroll-behavior**:

The [`overscroll-behavior`](https://developer.mozilla.org/docs/Web/CSS/overscroll-behavior) property allows you to prevent overflow scrolling leaking into a parent container (called scroll chaining).



