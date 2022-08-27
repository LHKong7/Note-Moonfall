# Filters

you can apply effects you might only think possible in a graphics application.



A combination of CSS filters and the `backdrop-filter` allow us to apply effects and blur what's needed in real time.



##### The filter property



**blur**: applies a gaussian blur and the only argument you can pass is a `radius` which is how much blur is applied.

```css
.my-element {
	filter: blur(0.2em);
}
```



**brightness**: To increase or decrease the brightness of an element, use the brightness function. The brightness value is expressed as a percentage with the unchanged image being expressed as a value of 100%. 



**contrast**: Set a value between 0% and 100% to decrease or increase the contrast, respectively.



**grayscale**: You can apply a completely grayscale effect by using `1` as a value for `grayscale()`, or `0` to have a completely saturated element. 



**invert**: you can pass `1` or `0` to the `invert()` function to turn it on or off. When it is on, the element's colors are completely inverted.



**opacity** : where you can pass a number or percentage to increase or reduce opacity. If you pass no arguments, the element is fully visible.



**saturate** :  increases or decreases color saturation.



**sepia** :  The sepia tone is a photographic printing technique that converts black tones to brown tones to warm them up.



**hue-rotate**:  You learned about how the hue in `hsl` references a rotation of the color wheel in the [colors lesson](https://web.dev/learn/css/color) and this filter works in a similar way.



**drop-shadow** : You can apply a curve-hugging drop shadow like you would in a design tool, such as Photoshop with [`drop-shadow`](https://developer.mozilla.org/docs/Web/CSS/filter-function/drop-shadow())



**url**: The `url` filter allows you to apply an SVG filter from a linked SVG element or file. 



