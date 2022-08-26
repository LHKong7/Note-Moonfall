# Focus



Focus styles assist people who use a device such as a keyboard or a switch control to navigate and interact with a website. If an element receives focus and there is no visual indication, a user may lose track of what is in focus.



##### How elements get focus

Certain elements are automatically focusable; These are elements that accept interaction and input such as, `<a>` , `<button>`, `<input`> and `<select>` . In short, all form elements, button and links.

To interact with focusable elements: 

- using tab key to move forward on the page
- shift+tab to move backward

There is also a HTML attribute called `tabindex` which allows you to change the tabbing index—which is order in which elements are focused—every time someone presses their tab key, or focus is shifted with a hash change in the URL or by a JavaScript event.



**tabindex**: 

- 0 : it can receive focus via the tab key and it will honour the global tab index which is defined by the document source order.

- -1 : it can only receive focus programmatically, which means only when a JS event happens or a hash change (matching the element's id in the URL ) occurs
- higher than 0 : it will removed from the global tab index, defined by document source order.



##### Styling focus

The default browser behaviro when an element receives focus is to present a focus ring. This focus ring varies between both browser and OS.



This behavior can be changed with CSS, using `:focus` , `:focus-within` and `:focus-visible` pseudo classes.



It is important to set a focus style which has **contrast** with the default style of an element. For example, a common approach is to utilize the `outline` property.

```
a:focus {
  outline: 2px solid slateblue;
}
```



