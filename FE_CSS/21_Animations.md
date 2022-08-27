# Animations

Animation is a great way to highlight interactive elements.



CSS Animation: allow users to set an animation sequence, using keyframes. Animations can be simple, one state animation or even complex, time-based sequences.



##### What is a keyframe

Keyframes are the mechanism that you use to assign animation states to timestamps, along a timeline.



**@keyframes**: (The browser will take the current state of the element as a keyframe, so at minimum, 1 keyframe is required.)

```css
@keyframes my-animation {
	from {
		transform: translateY(20px);
	}
	to {
		transform: translateY(0px);
	}
}
```

The first part to note is the [custom ident](https://developer.mozilla.org/docs/Web/CSS/custom-ident) (custom identifier)—or in more human terms, the name of the keyframes rule. This rule's identifier is `my-animation`. The custom identifier works like a function name. 



Inside the keyframes rule, `from` and `to` are keywords that represent `0%` and `100%`, which are the start of the animation and end. 



##### The animation properties

To use the `@keyframes` in a CSS rule, define various animation properties or, use the `animation` shorthand property.



**animation-duration**: define how long the `@keyframes` timeline should be. It should be a time value. It defaults to 0 seconds, which means the animation still runs, but it will too quick to see.



**animation-timing-function**: (Easing) To help recreate natural motion in animation. The timing function to calculate the speed of an animation at each point. Calculated values are often curved, making the animation run at variable speds over the course of `animation-duration` .

There are several keywords available as presets in CSS, which are used as the value for [animation-timing-function](https://developer.mozilla.org/docs/Web/CSS/animation-timing-function): `linear`, `ease`, `ease-in`, `ease-out`, `ease-in-out`.

In CSS, you can define a bézier curve directly, using the `cubic-bezier()` function, which accepts four number values: `x1`, `y1`, `x2`, `y2`.

`steps()` : easing function lets you break the timeline into defined, equal intervals.





**animation-iteration-count**: defines how many times the `@keyframes` timeline should run.

You can use the `infinite` keyword which will loop your animation, which is how the "pulser" demo from the start of this lesson works.



**animation-direction**: 

You can set which direction the timeline runs over your keyframes with [animation-direction](https://developer.mozilla.org/docs/Web/CSS/animation-direction):

- Normal: the default value which is forwards
- reverse : runs backwards over the timeline
- Alternate: for each animation iteration, the timeline will run forwards or backwards in sequence
- `alternate-reverse` : the reverse of alternate



**animation-delay**: defines how long to wait before starting the animation



**animation-play-state**: allows user to play and pause the animation. The default value is `runing` and if you set to `paused` it will pause the animation



**animation-fill-mode**: defines which values in the `@keyframes` timeline persist before the animation starts or after it ends. The default value is `none` which means when the animation is complete, the values in the timeline are discarded. Other options:

- `forwards`: The last keyframe will persist, based on the animation direction.
- `backwards`: The first keyframe will persist, based on the animation direction.
- `both`: follows the rules for both `forwards` and `backwards`.



**Animation shorthand**:

1. `animation-name`
2. `animation-duration`
3. `animation-timing-function`
4. `animation-delay`
5. `animation-iteration-count`
6. `animation-direction`
7. `animation-fill-mode`
8. `animation-play-state`



##### Considerations when working with animation

Users can define in their operating system that they prefer to reduce motion experienced when they interact with applications and websites. This preference can be detected using the [prefers-reduced-motion](https://developer.mozilla.org/docs/Web/CSS/@media/prefers-reduced-motion) media query.



```css
@media (prefers-reduced-motion) {
  .my-autoplaying-animation {
    animation-play-state: paused;
  }
}

```