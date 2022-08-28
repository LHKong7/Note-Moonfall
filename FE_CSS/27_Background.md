# Backgrounds



CSS provides a variety of ways to make meaningful changes to it–including allowing multiple backgrounds.



### Backgrounds

Behind every CSS box is a specialized layer called the **background layer**. CSS provides a variety of ways to make meaningful changes to it-including allowing multiple backgrounds.



Background layers are furthest from the user, rendered behind the contents of a box starting from its `padding-box` region. This enables the background layer to not overlap with borders at all.





### Background color

One of the simplest effects you can apply to a background layer is setting the [color](https://web.dev/learn/css/color/). The initial value of `background-color` is `transparent`, which allows the contents of a parent to be visible.



### Background images

One top of the `background-color` layer, you can add a background image, using the `background-image` property. A background-image accepts the following:

- An image URL or data URL using the `url` CSS function
- An image dynamically created by a gradient CSS function



**CSS gradient backgrounds**:

Serveral gradient CSS functions exist to allow users to generate a background-image, when passed two or more colors.

**Repeating background images**:

By default, background images repeat horizontally and vertically to fill the entire space of the background layer.

`background-repeat` property with one of the following values:

- `repeat` : the images within the space available, cropping as necessary.
- `round` : The image repeats hortizontally and vertically to fit as many instances into the space available, without cropping, compressing or stretching
- `space` : The image repeats horizontally and vertically to fit as many instances within the space available without cropping—spacing out instances of the image as needed. Repeating images touch the edges of the space a background layer occupies, with white space evenly distributed between them.



### Background position

The initial position of background images is top left. The `background-position` property allows you to change this behavior by offsetting the image position.

`background-position` property allows you to position images along the x and y axis independently with two values by default.





### Background size

The `background-size` property sets the size of background images; By default background images are sized based on their intrinsic (actual) width, height, and aspect ratio.

The `background-size` property uses CSS length and percentage values or specific keywords. The property accepts up to two parameters corresponding to allowing you to change width and height of a background independently.



Keywords:

- auto
- cover: Covers the entire area of the background layer.
- contain: Sizes the image to fill the space without stretching or cropping. 



### Background attachment

The `background-attachment` property enables you to modify the fixed position behavior of background images (images part of a background layer) once the layer is visible on a screen.

It accepts 3 keywords: `scroll`, `fixed`, and `local`.



### Background Origin

The `background-origin` property enables you to modify the area of backgrounds associated with a particular box. The values the property accepts correspond to the `border-box` , `padding-box`, and `content-box` regions of a box .



### Background Clip

The `background-clip` property controls what is visually seen from a background layer regardless of the bounds created by the `background-origin` property.





### Multiple Backgrounds

As mentioned at the beginning of the module, the background layer allows multiple sublayers to be defined. For brevity, I'll refer to these sublayers as backgrounds.



Multiple backgrounds are defined top to bottom; The first background is the closest to the user, while the last background is the furthest from the user.



```css
background:
  <background-image>
  <background-position> / <background-size>?
  <background-repeat>
  <background-attachment>
  <background-origin>
  <background-clip>
  <background-color>?
```

