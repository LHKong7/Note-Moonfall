# Transitions

Using CSS transitions, we can interpolate between the initial state and the target state of the element. The transition between the two enhances the user experience by providing visual direction, support, and hints about the cause and effect of the interaction.



*Interpolation* is the process of creating "in-between" steps that smoothly transition from one state to another.

#### Transition properties

**transition-property**: specifies which style(s) to transition. The property accepts one or more CSS property names in a comma-separated list. Optionally, you may use `transition-property: all` to indicate that every property should transition.

**transition-duration**: used to define the length of time that a transition will take to complete.

**transition-timing-function**: vary the speed of a CSS transition over the course of the `transition-duration`.

**transition-delay**: specify the time at which a transition will start. If `transition-duration` is not specified, transitions will start instantly because the default value is `0s`



#### What can and cannot transition

**Transform**:  The [`transform`](https://developer.mozilla.org/docs/Web/CSS/transform) CSS property is commonly transitioned because it is a GPU-accelerated property that results in smoother animation that also consumes less battery. This property lets you arbitrarily scale, rotate, translate, or skew an element.



**Color**: The `color`, `background-color`, and `border-color` properties are just a few places where color can be transitioned upon interaction.



**Shadows**: Shadows are often transitioned to indicate elevation change, like from user focus.



**Filters**: a powerful CSS property that lets you add graphic effects on the fly. Transitioning between different `filter` states can create some pretty impressive results.



#### Transition triggers

Below is a list of some pseudo-classes and events that can trigger state changes in your elements.

- [`:hover`](https://web.dev/learn/css/pseudo-classes/#:hover): matches if the cursor is over the element.
- [`:focus`](https://web.dev/learn/css/pseudo-classes/#:focus-:focus-within-and-:focus-visible): matches if the element is focused.
- [`:focus-within`](https://web.dev/learn/css/pseudo-classes/#:focus-:focus-within-and-:focus-visible) : matches if the element or any of its descendants are focused.
- [`:target`](https://web.dev/learn/css/pseudo-classes/#:target): matches when the current URL's [fragment](https://developer.mozilla.org/docs/Web/HTTP/Basics_of_HTTP/Identifying_resources_on_the_Web#fragment) matches the element's id.
- [`:active`](https://web.dev/learn/css/pseudo-classes/#:active): matches when the element is being activated (typically when the mouse is pressed over it).
- `class` change from JavaScript: when an element's CSS `class` changes via JavaScript, CSS will transition eligible properties that have changed.





##### Different transitions for enter or exit



##### Accessibility considerations && Performance considerations

CSS has a media feature called [`prefers-reduced-motion`](https://developer.mozilla.org/docs/Web/CSS/@media/prefers-reduced-motion) that detects if a user has indicated a preference for less motion from their device.

When working with CSS transitions, you may encounter performance issues if you add transitions for certain CSS properties. For example, when properties such as `width` or `height` change, they push content around on the rest of the page. This forces CSS to calculate new positions for every affected element for each frame of the transition. When possible, we recommend using properties like `transform` and `opacity` instead.



