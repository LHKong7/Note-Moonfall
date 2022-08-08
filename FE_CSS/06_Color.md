# Color



CSS有着很多种数据类型：strings，或者numbers。



**Hex Colors**: Hex是一种RGB语法的缩写， which assigns a numeric value to red, green and blue which are three primary colors.

​	Hexadecimal ranges are `0-9` and `A-F`. 当在six disgit sequence时， 他们转变成 RGB numerical ranges which are 0-255 which

correspond to the red， green and blue channels respecitively。 同样也可以定义Alpha 值 （代表percentage of transparency）

- 0% alpha—which is fully transparent—is **00**: `#00000000`
- 50% alpha is **80**: `#00000080`
- 75% alpha is **BF**: `#000000BF`



To convert a two digit hex to a decimal, take the first digit and multiply it by 16 (because hex is base 16), then add the second digit. Using **BF** as an example for 75% alpha:

1. B is equal to 11, which when multiplied by 16 equals 176
2. F is equal to 15
3. 176 + 15 = 191
4. The alpha value is 191—75% of 255



**RGB (Red, Green, Blue)**:

RGB Colors 使用 `rgb()` 颜色函数定义， 使用  numbers 或者 percentages 作为 parameters

- The numbers need to be within the **0-255** range
-  the percentages are between **0% and 100%‌**



**HSL (Hue, Saturation, Lightness)**:

HSL stands for hue, saturation and lightness. Hue describes the value on the color wheel, from 0 to 360 degrees, starting with red (being both 0 and 360). A hue of 180, or 50% would be in the blue range. It's the origin of the color that we see.

Saturation is how vibrant the selected hue is. A fully desaturated color (with a saturation of `0%`) will appear grayscale. 

Lightness is the parameter which describes the scale from white to black of added light. A lightness of `100%` will always give you white.



Special Keywords:

- `transparent` is a fully transparent color. It is also the initial value of `background-color`
- `currentColor` is the contextual computed dynamic value of the `color` property. If you have a text color of `red` and then set the `border-color` to be `currentColor`, it will also be red. If the element that you define `currentColor` on doesn't have a value for `color` defined, `currentColor` will be computed by the cascade instead





**Where to use Color in CSS rules**:

styling text: use `color`, `text-shadow` and `text-decoration-color`

Background: `background` or `background-color`

gradiens: `linear-gradient`  Gradients are a type of image that can be programmatically defined in CSS. Gradients accept two or more colors in any combination of color format, such as hex, rgb or hsl.

`border-color`, and `outline-color` set the color for borders and outlines on your boxes. The `box-shadow` property also accepts color as one of the values.











