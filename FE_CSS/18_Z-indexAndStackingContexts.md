# Z-index and stacking contexts



##### Z-index

`z-index` property explicitly sets a layer order for HTML based on the 3D space of the browser -> Z axis, this is the axis which shows which layers are closer to and further from users.



In normal flow, if you set a specific value for `z-index` and it isn't working, you need to set the element's `position` value to anything other than `static`. This is a common place where people struggle with `z-index`. 

​	This isn't the case if you are in a flexbox or grid context, though, because you can modify the z-index of flex or grid items without adding `position: relative`.



##### Stacking Context

A stacking context is a group of elements that have a common parent and move up and down the z axis together.



**Creating a stacking context**: You don't need to apply `z-index` and `position` to create a new [stacking context](https://developer.mozilla.org/docs/Web/CSS/CSS_Positioning/Understanding_z_index/The_stacking_context). You can create a new stacking context by adding a value for properties which create a new composite layer such as `opacity`, `will-change` and `transform`.

