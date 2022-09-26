# Browser rendering optimization



16 milliseconds per frame

Making a frame (Single Frame): 

​	make HTTP request -> lookaheadparse, (parse HTML), DOM -> CSS stylesheet -> Combine DOM and CSS into render TREE.

​	The only elements that will actually be displayed on the page will make it into the render tree (pseudoEl :before, after will displayed in the render tree and display none element will not make into the render tree)



Reflow: layout change ()

raster: 



