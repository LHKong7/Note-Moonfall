# Pseudo-Classes

Pseudo-classes let you apply CSS based on state changes. This means that your design can react to user input.



A pseudo-class lets you apply styles based on state changes and external factors. This means that your design can react to user input such as an invalid email addres. 

Pseudo-class hook onto specific state that an element might be in, rather than generally style parts of that element.



##### interactive States

`:hover` : if a user has a pointing device like a mouse or trackpad and they place it over an element, you can hook onto that state with `:hover` to apply styles.



`:active`  : This state is triggered when an element is actively being interacted with -- such as a click -- before click is released. If a pointing device like a mouse is used, this state is when the click starts and hasn't yet been released.



`:focus`, `:focus-within`, and `:focus-visible` : 

- If an element can receive focus—like a `<button>`— you can react to that state with the [`:focus`](https://developer.mozilla.org/docs/Web/CSS/:focus) pseudo-class.
- You can also react if a child element of your element receives focus with [`:focus-within`](https://developer.mozilla.org/docs/Web/CSS/:focus-within).
-  With [`:focus-visible`](https://developer.mozilla.org/docs/Web/CSS/:focus-visible) you can present a focus style when an element receives focus via the keyboard, while also using the `outline: none` rule to prevent it when a pointer device interacts with it.



`:target`: selects an element that has an `id` matching a URL fragment.



***Order matters*** : If you define a `:visited` style, it can be overridden by a link pseudo-class with at least equal specificity. Because of this, it's recommended that you use the LVHA rule for styling links with pseudo-classes in a particular order: `:link`, `:visited`, `:hover`, `:active`.



##### Form States

`:disabled` && `:enabled` 

If a form element, such as a `<button>` is disabled by the browser, you can hook on to that state with the [`:disabled`](https://developer.mozilla.org/docs/Web/CSS/:disabled) pseudo-class.

The [`:enabled`](https://developer.mozilla.org/docs/Web/CSS/:enabled) pseudo-class is available for the opposite state, though form elements are also `:enabled` by default, therefore you might not find yourself reaching for this pseudo-class.



`:checked` && `:indeterminate` : 

- The [`:checked`](https://developer.mozilla.org/docs/Web/CSS/:checked) pseudo-class is available when a supporting form element, such as a checkbox or radio button is in a checked state.

  The `:checked` state is a binary(true or false) state, but checkboxes do have an in-between state when they are neither checked or unchecked. This is known as the [`:indeterminate`](https://developer.mozilla.org/docs/Web/CSS/:indeterminate) state.

- 



`placeholder-shown`





##### Selecting elements by their index, order and occurrence

