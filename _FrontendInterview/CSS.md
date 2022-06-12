## CSS

[TOC]



##### 列出display的值并说明他们的作用？

```
display： none | inline | block | list-item | inline-block | table | inline-table | table-caption | table-cell | table-row | table-row-group | table-column | table-column-group | table-footer-group | table-header-group | run-in | box | inline-box | flexbox | inline-flexbox | flex | inline-flex
默认值：inline

none： 隐藏对象。与visibility属性的hidden值不同，其不为被隐藏的对象保留其物理空间 
inline： 指定对象为内联元素。 
block： 指定对象为块元素。 
list-item： 指定对象为列表项目。 
inline-block： 指定对象为内联块元素。（CSS2） 
table： 指定对象作为块元素级的表格。类同于html标签<table>（CSS2） 
inline-table： 指定对象作为内联元素级的表格。类同于html标签<table>（CSS2） 
table-caption： 指定对象作为表格标题。类同于html标签<caption>（CSS2） 
table-cell： 指定对象作为表格单元格。类同于html标签<td>（CSS2） 
table-row： 指定对象作为表格行。类同于html标签<tr>（CSS2） 
table-row-group： 指定对象作为表格行组。类同于html标签<tbody>（CSS2） 
table-column： 指定对象作为表格列。类同于html标签<col>（CSS2） 
table-column-group： 指定对象作为表格列组显示。类同于html标签<colgroup>（CSS2） 
table-header-group： 指定对象作为表格标题组。类同于html标签<thead>（CSS2） 
table-footer-group： 指定对象作为表格脚注组。类同于html标签<tfoot>（CSS2） 
run-in： 根据上下文决定对象是内联对象还是块级对象。（CSS3） 
box： 将对象作为弹性伸缩盒显示。（伸缩盒最老版本）（CSS3） 
inline-box： 将对象作为内联块级弹性伸缩盒显示。（伸缩盒最老版本）（CSS3） 
flexbox： 将对象作为弹性伸缩盒显示。（伸缩盒过渡版本）（CSS3） 
inline-flexbox： 将对象作为内联块级弹性伸缩盒显示。（伸缩盒过渡版本）（CSS3） 
flex： 将对象作为弹性伸缩盒显示。（伸缩盒最新版本）（CSS3） 
inline-flex： 将对象作为内联块级弹性伸缩盒显示。（伸缩盒最新版本）（CSS3）
```



##### 如何居中div, 如何居中一个浮动元素?

(1)、非浮动元素居中：

​	可以设置 margin:0 auto 令其居中, 定位 ,父级元素text-align:center等等

(2)、浮动元素居中:
方法一:设置当前div的宽度，然后设置margin-left:50%; position:relative; left:-250px;其中的left是宽度的一半。
方法二:父元素和子元素同时左浮动，然后父元素相对左移动50%，再然后子元素相对左移动-50%。
方法三:position定位等等。



##### CSS中 link 和@import 的区别是？

(1)、link属于HTML标签，而@import是CSS提供的; 
(2)、页面被加载的时，link会同时被加载，而@import引用的CSS会等到页面被加载完再加载;
(3)、import只在IE5以上才能识别，而link是HTML标签，无兼容问题;
(4)、link方式的样式的权重 高于@import的权重.



##### 请列举几种清除浮动的方法(至少两种)?

**(1)、父级div定义 height** 
原理：父级div手动定义height，就解决了父级div无法自动获取到高度的问题。 
优点：简单、代码少、容易掌握 
缺点：只适合高度固定的布局，要给出精确的高度，如果高度和父级div不一样时，会产生问题 
建议：不推荐使用，只建议高度固定的布局时使用
**(2)、结尾处加空div标签 clear:both** 
原理：添加一个空div，利用css提高的clear:both清除浮动，让父级div能自动获取到高度 
优点：简单、代码少、浏览器支持好、不容易出现怪问题 
缺点：不少初学者不理解原理；如果页面浮动布局多，就要增加很多空div，让人感觉很不好 
建议：不推荐使用，但此方法是以前主要使用的一种清除浮动方法 
**(3)、父级div定义 伪类:after 和 zoom** 
原理：IE8以上和非IE浏览器才支持:after，原理和方法2有点类似，zoom(IE转有属性)可解决ie6,ie7浮动问题 
优点：浏览器支持好、不容易出现怪问题（目前：大型网站都有使用，如：腾迅，网易，新浪等等） 
缺点：代码多、不少初学者不理解原理，要两句代码结合使用才能让主流浏览器都支持。
建议：推荐使用，建议定义公共类，以减少CSS代码。
**(4)、父级div定义 overflow:hidden** 
原理：必须定义width或zoom:1，同时不能定义height，使用overflow:hidden时，浏览器会自动检查浮动区域的高度 
优点：简单、代码少、浏览器支持好 
缺点：不能和position配合使用，因为超出的尺寸的会被隐藏。 
建议：只推荐没有使用position或对overflow:hidden理解比较深的朋友使用。 
**(5)、父级div定义 overflow:auto** 
原理：必须定义width或zoom:1，同时不能定义height，使用overflow:auto时，浏览器会自动检查浮动区域的高度 
优点：简单、代码少、浏览器支持好 
缺点：内部宽高超过父级div时，会出现滚动条。 
建议：不推荐使用，如果你需要出现滚动条或者确保你的代码不会出现滚动条就使用吧。



##### block，inline和inlinke-block细节对比？

**• display:block**
a、block元素会独占一行，多个block元素会各自新起一行。默认情况下，block元素宽度自动填满其父元素宽度。
b、block元素可以设置width,height属性。块级元素即使设置了宽度,仍然是独占一行。
c、block元素可以设置margin和padding属性。
**• display:inline**
a、inline元素不会独占一行，多个相邻的行内元素会排列在同一行里，直到一行排列不下，才会新换一行，其宽度随元素的内容而变化。
b、inline元素设置width,height属性无效。
c、inline元素的margin和padding属性，水平方向的padding-left, padding-right, margin-left, margin-right都产生边距效果；但竖直方向的padding-top, padding-bottom, margin-top, margin-bottom不会产生边距效果。
**• display:inline-block**
a、简单来说就是将对象呈现为inline对象，但是对象的内容作为block对象呈现。之后的内联对象会被排列在同一行内。比如我们可以给一个link（a元素）inline-block属性值，使其既具有block的宽度高度特性又具有inline的同行特性。
**补充说明**
a、一般我们会用display:block，display:inline或者display:inline-block来调整元素的布局级别，其实display的参数远远不止这三种，仅仅是比较常用而已。
b、IE（低版本IE）本来是不支持inline-block的，所以在IE中对内联元素使用display:inline-block，理论上IE是不识别的，但使用display:inline-block在IE下会触发layout，从而使内联元素拥有了display:inline-block属性的表象。



##### 说说浮动元素会引起的问题和你的解决办法

（1）父元素的高度无法被撑开，影响与父元素同级的元素
（2）与浮动元素同级的非浮动元素会跟随其后
（3）若非第一个元素浮动，则该元素之前的元素也需要浮动，否则会影响页面显示的结构

使用CSS中的clear:both;属性来清除元素的浮动可解决问题(2)、(3)

对于问题(1)，添加如下样式，给父元素添加clearfix样式：

```css
.clearfix:after{content: ".";display: block;height: 0;clear: both;visibility: hidden;}
.clearfix{display: inline-block;} /* for IE/Mac */
```

**清除浮动的几种方法：**

1. 额外标签法，<div style="clear:both;"></div>（缺点：不过这个办法会增加额外的标签使HTML结构看起来不够简洁。）

2. 使用after伪类

   ```css
   #parent:after{
     content:" ";
     height:0;
     visibility:hidden;
     display:block;
     clear:both;
   }
   ```

   

3. 浮动外部元素

4. 设置`overflow`为`hidden`或者auto



##### 为什么要初始化CSS样式？

因为浏览器的兼容问题，不同浏览器对有些标签的默认值是不同的，如果没对CSS初始化往往会出现浏览器之间的页面显示差异。
当然，初始化样式会对SEO有一定的影响，但鱼和熊掌不可兼得，但力求影响最小的情况下初始化。
*最简单的初始化方法就是： * {padding: 0; margin: 0;} （不建议）



##### 解释下浮动和它的工作原理？清除浮动的技巧？

浮动元素脱离文档流，不占据空间。浮动元素碰到包含它的边框或者浮动元素的边框停留。
**(1)、使用空标签清除浮动。**
这种方法是在所有浮动标签后面添加一个空标签 定义css clear:both. 弊端就是增加了无意义标签。
**(2)、使用overflow。**
给包含浮动元素的父标签添加css属性 overflow:auto; zoom:1; zoom:1用于兼容IE6。
**(3)、使用after伪对象清除浮动。**
该方法只适用于非IE浏览器。具体写法可参照以下示例。使用中需注意以下几点。一、该方法中必须为需要清除浮动元素的伪对象中设置 height:0，否则该元素会比实际高出若干像素；



##### 谈谈你对CSS中刻度的认识？

**在CSS中刻度是用于设置元素尺寸的单位。**
a、特殊值0可以省略单位。例如：margin:0px可以写成margin:0 
b、一些属性可能允许有负长度值，或者有一定的范围限制。如果不支持负长度值，那应该变换到能够被支持的最近的一个长度值。 
c、长度单位包括：相对单位和绝对单位。 
相对长度单位有： em, ex, ch, rem, vw, vh, vmax, vmin 
绝对长度单位有： cm, mm, q, in, pt, pc, px
绝对长度单位：1in = 2.54cm = 25.4 mm = 72pt = 6pc = 96px
**文本相对长度单位：em**
相对长度单位是相对于当前对象内文本的字体尺寸，如当前对行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸。(相对父元素的字体大小倍数)
body { font-size: 14px; }
h1 { font-size: 16px; }
.size1 p { font-size: 1em; }
.size2 p { font-size: 2em; }
.size3 p { font-size: 3em; }
**文本相对长度单位：rem**
rem是CSS3新增的一个相对单位（root em，根em），相对于根元素(即html元素)font-size计算值的倍数
只相对于根元素的大小
浏览器的默认字体大小为16像素，浏览器默认样式也称为user agent stylesheet，就是所有浏览器内置的默认样式，多数是可以被修改的，但chrome不能直接修改，可以被用户样式覆盖。

**rem**
rem是CSS3新增的一个相对单位（root em，根em），相对于根元素(即html元素)font-size计算值的倍数
只相对于根元素的大小
rem（font size of the root element）是指相对于根元素的字体大小的单位。简单的说它就是一个相对单位。
作用：利用rem可以实现简单的响应式布局，可以利用html元素中字体的大小与屏幕间的比值设置font-size的值实现当屏幕分辨率变化时让元素也变化，以前的天猫tmall就使用这种办法
**em**
文本相对长度单位。相对于当前对象内文本的字体尺寸。如当前对行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸(默认16px)。(相对父元素的字体大小倍数)
em（font size of the element）是指相对于父元素的字体大小的单位。它与rem之间其实很相似，区别在。（相对是的HTML元素的字体大，默认16px）
**em与rem的重要区别：** 它们计算的规则一个是依赖父元素另一个是依赖根元素计算



##### 请你说说em与rem的区别？

**rem**
rem是CSS3新增的一个相对单位（root em，根em），相对于根元素(即html元素)font-size计算值的倍数
只相对于根元素的大小
rem（font size of the root element）是指相对于根元素的字体大小的单位。简单的说它就是一个相对单位。
作用：利用rem可以实现简单的响应式布局，可以利用html元素中字体的大小与屏幕间的比值设置font-size的值实现当屏幕分辨率变化时让元素也变化，以前的天猫tmall就使用这种办法
**em**
文本相对长度单位。相对于当前对象内文本的字体尺寸。如当前对行内文本的字体尺寸未被人为设置，则相对于浏览器的默认字体尺寸(默认16px)。(相对父元素的字体大小倍数)
em（font size of the element）是指相对于父元素的字体大小的单位。它与rem之间其实很相似，区别在。（相对是的HTML元素的字体大，默认16px）
**em与rem的重要区别：** 它们计算的规则一个是依赖父元素另一个是依赖根元素计算



##### 请你说说box-sizing属性的的用法？

设置或检索对象的盒模型组成模式

**a、box-sizing:content-box：** padding和border不被包含在定义的width和height之内。对象的实际宽度等于设置的width值和border、padding之和，即 ( Element width = width + border + padding，但占有页面位置还要加上margin ) 此属性表现为标准模式下的盒模型。
**b、box-sizing:border-box：** padding和border被包含在定义的width和height之内。对象的实际宽度就等于设置的width值，即使定义有border和padding也不会改变对象的实际宽度，即 ( Element width = width ) 此属性表现为怪异模式下的盒模型。



##### 说说你对边距折叠的理解?

**外边距折叠：** 相邻的两个或多个外边距 (margin) 在垂直方向会合并成一个外边距（margin）
**相邻：** 没有被非空内容、padding、border 或 clear 分隔开的margin特性. 非空内容就是说这元素之间要么是兄弟关系或者父子关系
**垂直方向外边距合并计算:**
a、参加折叠的margin都是正值：取其中 margin 较大的值为最终 margin 值。
b、参与折叠的 margin 都是负值：取的是其中绝对值较大的，然后，从 0 位置，负向位移。
c、参与折叠的 margin 中有正值，有负值：先取出负 margin 中绝对值中最大的，然后，和正 margin 值中最大的 margin 相加



##### 内联与块级标签有何区别？

Html中的标签默认主要分为两大类型，一类为块级元素，另一类是行内元素，许多人也把行内称为内联，所以叫内联元素，其实就是一个意思。为了很好的布局，必须理解它们间的区别。



##### 说说隐藏元素的方式有哪些？

a、使用CSS的display:none，不会占有原来的位置
b、使用CSS的visibility:hidden，会占有原来的位置
c、使用HTML5中的新增属性hidden="hidden"，不会占有原来的位置



##### 为什么重置浏览器默认样式，如何重置默浏览器认样式？

每种浏览器都有一套默认的样式表，即user agent stylesheet，网页在没有指定的样式时，按浏览器内置的样式表来渲染。这是合理的，像word中也有一些预留样式，可以让我们的排版更美观整齐。不同浏览器甚至同一浏览器不同版本的默认样式是不同的。但这样会有很多兼容问题。

a、最简单的办法：（不推荐使用）*{margin: 0;padding: 0;}。

b、使用CSSReset可以将所有浏览器默认样式设置成一样。

c、normalize：也许有些cssreset过于简单粗暴，有点伤及无辜，normalize是另一个选择。bootstrap已经引用该css来重置浏览器默认样式，比普通的cssreset要精细一些，保留浏览器有用的默认样式，支持包括手机浏览器在内的超多浏览器，同时对HTML5元素、排版、列表、嵌入的内容、表单和表格都进行了一般化。

天猫 使用的css reset重置浏览器默认样式



##### 谈谈你对BFC与IFC的理解？(是什么，如何产生，作用)

(1)、什么是BFC与IFC
a、BFC（Block Formatting Context）即“块级格式化上下文”， IFC（Inline Formatting Context）即行内格式化上下文。常规流（也称标准流、普通流）是一个文档在被显示时最常见的布局形态。一个框在常规流中必须属于一个格式化上下文，你可以把BFC想象成一个大箱子，箱子外边的元素将不与箱子内的元素产生作用。

b、BFC是W3C CSS 2.1 规范中的一个概念，它决定了元素如何对其内容进行定位，以及与其他元素的关系和相互作用。当涉及到可视化布局的时候，Block Formatting Context提供了一个环境，HTML元素在这个环境中按照一定规则进行布局。一个环境中的元素不会影响到其它环境中的布局。比如浮动元素会形成BFC，浮动元素内部子元素的主要受该浮动元素影响，两个浮动元素之间是互不影响的。也可以说BFC就是一个作用范围。

c、在普通流中的 Box(框) 属于一种 formatting context(格式化上下文) ，类型可以是 block ，或者是 inline ，但不能同时属于这两者。并且， Block boxes(块框) 在 block formatting context(块格式化上下文) 里格式化， Inline boxes(块内框) 则在 Inline Formatting Context(行内格式化上下文) 里格式化。

(2)、如何产生BFC
当一个HTML元素满足下面条件的任何一点，都可以产生Block Formatting Context：
a、float的值不为none
b、overflow的值不为visible
c、display的值为table-cell, table-caption, inline-block中的任何一个
d、position的值不为relative和static

CSS3触发BFC方式则可以简单描述为：在元素定位非static，relative的情况下触发，float也是一种定位方式。

(3)、BFC的作用与特点
a、不和浮动元素重叠，清除外部浮动，阻止浮动元素覆盖

如果一个浮动元素后面跟着一个非浮动的元素，那么就会产生一个重叠的现象。常规流（也称标准流、普通流）是一个文档在被显示时最常见的布局形态，当float不为none时，position为absolute、fixed时元素将脱离标准流



##### 说说你对页面中使用定位(position)的理解？

使用css布局position非常重要，语法如下：
position：static | relative | absolute | fixed | center | page | sticky
默认值：static，center、page、sticky是CSS3中新增加的值。
**(1)、static**
可以认为静态的，默认元素都是静态的定位，对象遵循常规流。此时4个定位偏移属性不会被应用，也就是使用left，right，bottom，top将不会生效。
**(2)、relative**
相对定位，对象遵循常规流，并且参照自身在常规流中的位置通过top，right，bottom，left这4个定位偏移属性进行偏移时不会影响常规流中的任何元素。
**(3)、absolute**
a、绝对定位，对象脱离常规流，此时偏移属性参照的是离自身最近的定位祖先元素，如果没有定位的祖先元素，则一直回溯到body元素。盒子的偏移位置不影响常规流中的任何元素，其margin不与其他任何margin折叠。
b、元素定位参考的是离自身最近的定位祖先元素，要满足两个条件，第一个是自己的祖先元素，可以是父元素也可以是父元素的父元素，一直找，如果没有则选择body为对照对象。第二个条件是要求祖先元素必须定位，通俗说就是position的属性值为非static都行。
**(4)、fixed**
固定定位，与absolute一致，但偏移定位是以窗口为参考。当出现滚动条时，对象不会随着滚动。
**(5)、center**
与absolute一致，但偏移定位是以定位祖先元素的中心点为参考。盒子在其包含容器垂直水平居中。（CSS3）
**(6)、page**
与absolute一致。元素在分页媒体或者区域块内，元素的包含块始终是初始包含块，否则取决于每个absolute模式。（CSS3）
**(7)、sticky**
对象在常态时遵循常规流。它就像是relative和fixed的合体，当在屏幕中时按常规流排版，当卷动到屏幕外时则表现如fixed。该属性的表现是现实中你见到的吸附效果。（CSS3）



##### 如何解决多个元素重叠问题？

**使用z-index属性可以设置元素的层叠顺序**

z-index属性
语法：z-index: auto | <integer>
默认值：auto
适用于：定位元素。即定义了position为非static的元素
取值：
auto： 元素在当前层叠上下文中的层叠级别是0。元素不会创建新的局部层叠上下文，除非它是根元素。 
整数： 用整数值来定义堆叠级别。可以为负值。 说明：
检索或设置对象的层叠顺序。 
z-index用于确定元素在当前层叠上下文中的层叠级别，并确定该元素是否创建新的局部层叠上下文。 
当多个元素层叠在一起时，数字大者将显示在上面。



##### 页面布局的方式有哪些？

方式：双飞翼、多栏、弹性、流式、瀑布流、响应式布局 

**双飞翼布局**

​	经典三列布局，也叫做圣杯布局【Holy Grail of Layouts】是Kevin Cornell在2006年提出的一个布局模型概念，在国内最早是由淘宝UED的工程师传播开来，在中国也有叫法是双飞翼布局，它的布局要求有几点：

a、三列布局，中间宽度自适应，两边定宽； 
b、中间栏要在浏览器中优先展示渲染； 
c、允许任意列的高度最高；
d、要求只用一个额外的DIV标签； 
e、要求用最简单的CSS、最少的HACK语句；

在不增加额外标签的情况下，圣杯布局已经非常完美，圣杯布局使用了相对定位，以后布局是有局限性的，而且宽度控制要改的地方也多。在淘宝UED（User Experience Design）探讨下，增加多一个div就可以不用相对布局了，只用到了浮动和负边距，这就是我们所说的双飞翼布局。

**多栏布局**

a、栏栅格系统：就是利用浮动实现的多栏布局，在bootstrap中用的非常多。
b、多列布局：栅格系统并没有真正实现分栏效果（如word中的分栏），CSS3为了满足这个要求增加了多列布局模块

**弹性布局（Flexbox）**

CSS3引入了一种新的布局模式——Flexbox布局，即伸缩布局盒模型（Flexible Box），用来提供一个更加有效的方式制定、调整和分布一个容器里项目布局，即使它们的大小是未知或者动态的，这里简称为Flex。
Flexbox布局常用于设计比较复杂的页面，可以轻松的实现屏幕和浏览器窗口大小发生变化时保持元素的相对位置和大小不变，同时减少了依赖于浮动布局实现元素位置的定义以及重置元素的大小。

Flexbox布局在定义伸缩项目大小时伸缩容器会预留一些可用空间，让你可以调节伸缩项目的相对大小和位置。例如，你可以确保伸缩容器中的多余空间平均分配多个伸缩项目，当然，如果你的伸缩容器没有足够大的空间放置伸缩项目时，浏览器会根据一定的比例减少伸缩项目的大小，使其不溢出伸缩容器。

综合而言，Flexbox布局功能主要具有以下几点：
a、屏幕和浏览器窗口大小发生改变也可以灵活调整布局；
b、可以指定伸缩项目沿着主轴或侧轴按比例分配额外空间（伸缩容器额外空间），从而调整伸缩项目的大小；
c、可以指定伸缩项目沿着主轴或侧轴将伸缩容器额外空间，分配到伸缩项目之前、之后或之间；
d、可以指定如何将垂直于元素布局轴的额外空间分布到该元素的周围；
e、可以控制元素在页面上的布局方向；
f、可以按照不同于文档对象模型（DOM）所指定排序方式对屏幕上的元素重新排序。也就是说可以在浏览器渲染中不按照文档流先后顺序重排伸缩项目顺序

**瀑布流布局**

瀑布流布局是流式布局的一种。是当下比较流行的一种网站页面布局，视觉表现为参差不齐的多栏布局，随着页面滚动条向下滚动，这种布局还会不断加载数据块并附加至当前尾部。最早采用此布局的网站是Pinterest，逐渐在国内流行开来。
**优点**
a、有效的降低了界面复杂度，节省了空间：我们不再需要臃肿复杂的页码导航链接或按钮了。
b、对触屏设备来说，交互方式更符合直觉：在移动应用的交互环境当中，通过向上滑动进行滚屏的操作已经成为最基本的用户习惯，而且所需要的操作精准程度远远低于点击链接或按钮。
c、更高的参与度：以上两点所带来的交互便捷性可以使用户将注意力更多的集中在内容而不是操作上，从而让他们更乐于沉浸在探索与浏览当中。
**缺点**
a、有限的用例：
无限滚动的方式只适用于某些特定类型产品当中一部分特定类型的内容。
例如，在电商网站当中，用户时常需要在商品列表与详情页面之间切换，这种情况下，传统的、带有页码导航的方式可以帮助用户更稳妥和准确的回到某个特定的列表页面当中。
b、额外的复杂度：
那些用来打造无限滚动的JS库虽然都自称很容易使用，但你总会需要在自己的产品中进行不同程度的定制化处理，以满足你们自己的需求;另外这些JS库在浏览器和设备兼容性等方面的表现也参差不齐，你必须做好充分的测试与调整工作。
c、再见了，页脚：
如果使用了比较典型的无限滚动加载模式，这就意味着你可以和页脚说拜拜了。
最好考虑一下页脚对于你的网站，特别是用户的重要性;如果其中确实有比较重要的内容或链接，那么最好换一种更传统和稳妥的方式。
千万不要耍弄你的用户，当他们一次次的浏览到页面底部，看到页脚，却因为自动加载的内容突然出现而无论如何都无法点击页脚中的链接时，他们会变的越发愤怒。
d、集中在一页当中动态加载数据，与一页一页的输出相比，究竟那种方式更利于SEO，这是你必须考虑的问题。对于某些以类型网站来说，在这方面进行冒险是很不划算的。
e、关于页面数量的印象：
其实站在用户的角度来看，这一点并非负面;不过，如果对于你的网站来说，通过更多的内容页面展示更多的相关信息(包括广告)是很重要的策略，那么单页无限滚动的方式对你并不适用。

**流式布局（Fluid）**

固定布局和流式布局在网页设计中最常用的两种布局方式。固定布局能呈现网页的原始设计效果，流式布局则不受窗口宽度影响，流式布局使用百分比宽度来限定布局元素，这样可以根据客户端分辨率的大小来进行合理的显示。

**响应式布局**

响应式布局是Ethan Marcotte在2010年5月份提出的一个概念，简而言之，就是一个网站能够兼容多个终端——而不是为每个终端做一个特定的版本。这个概念是为解决移动互联网浏览而诞生的。
响应式布局可以为不同终端的用户提供更加舒适的界面和更好的用户体验，而且随着目前大屏幕移动设备的普及，用“大势所趋”来形容也不为过。随着越来越多的设计师采用这个技术，我们不仅看到很多的创新，还看到了一些成形的模式。
**优点**
a、面对不同分辨率设备灵活性强
b、能够快捷解决多设备显示适应问题
**缺点**
a、兼容各种设备工作量大，效率低下
b、代码累赘，会出现隐藏无用的元素，加载时间加长
c、其实这是一种折中性质的设计解决方案，多方面因素影响而达不到最佳效果
d、一定程度上改变了网站原有的布局结构，会出现用户混淆的情况



##### **overflow** :hidden是否形成新的块级格式化上下文？

会形成，触发BFC的条件有：
\- float的值不为none。
\- overflow的值不为visible。
\- display的值为table-cell, table-caption, inline-block 中的任何一个。
\- position的值不为relative 和static。



##### 伪类和伪元素：

**伪类，更多的定义的是状态**。常见的伪类有 :hover，:active，:focus，:visited，:link，:not，:first-child，:last-child等等。

**伪元素，不存在于DOM树中的虚拟元素，它们可以像正常的html元素一样定义css，但无法使用JavaScript获取**。常见伪元素有 ::before，::after，::first-letter，::first-line等等。

**CSS3明确规定了，伪类用一个冒号(:)来表示，而伪元素则用两个冒号(::)来表示**。但目前因为兼容性的问题，它们的写法可以是一致的，都用一个冒号(:)就可以了，所以非常容易混淆。



表单的校验中，常会用到 `:required`、`:valid` 和 `:invalid` 这三个伪类。先来看看它们所代表的含义。

- :required，指定具有 required属性 的表单元素
- :valid，指定一个 匹配指定要求 的表单元素
- :invalid，指定一个 不匹配指定要求 的表单元素



折叠面板的显示或隐藏，只能用JavaScript来搞定。但是现在，可以用伪类 `:target` 来实现。 :target 是文档的内部链接，即 URL 后面跟有锚名称 #，指向文档内某个具体的元素。



当我们要指定一系列标签中的某个元素时，并不需要用JavaScript获取。可以用 `:nth-child(n)` 与 `:nth-of-type(n)` 来找到，并指定样式。但它们有一些小区别，需要注意。



##### 像素基本概念

手机（屏幕）尺寸： 指对角线的长度 用英寸表示

css像素：逻辑像素，也就是我们写代码时候的px，注意缩放会改变css像素大小。

设备像素pt ： 物理像素，不同的设备的物理像素大小也是不同的

ppi：像素密度，即每英寸（in）像素个数，常用于ui设计。

​			ppi = 屏幕分辨率的各方向的平方的和/屏幕尺寸

```
for example：

iphone6: 屏幕是 1334 * 750 326ppi 屏幕4.7 英寸
Math.sqrt(Math.pow(1334, 2) + Math.pow(750, 2)) / 4.7 = 325
```

dpi：每英寸（in）像素点数，常用于平面印刷

dpr像素比：

​				像素比 = 物理像素/css像素

​	在PC端：

​			dpr通常为1，即只需指定css为1，物理像素就为1px 因为屏幕足够大，一个css像素用一个物理像素来显示，完全可以

​	在移动端：

​			若dpr=2，意味着一个需要2个物理像素填充一个css像素，面积上需要4个，因此一个css像素=dpr个物理像素

​			移动设备大小是有限的，而且分辨率不低，甚至比pc端更高，也就是可以显示的物理像素更多，如果和pc端一样，一个css的px和物理像素一一对应,可以想象,显示的内容有多小



​	在高清屏中：

​		屏幕拥有的物理像素点数比非高清屏多4倍甚至更多,如果继续按照dpr=1,那么同一张图片在高清屏上面显示的区域面积会是非高清屏的1/4 	故推出dpr=4等等,使用4个乃至更多物理像素来渲染1个逻辑像素,这样一来,,同样的CSS代码设置的尺寸相同

​	

​	1px边框问题：

​		故在之上的条件下,1px可能屏幕硬是塞给你一条宽度为2—3个物理像素的线



单位：

​		em：一个字符的长度

​		in：英尺

分辨率：狭义的理解为屏幕的像素,例如1200*780,可以理解为水平方向有1200的像素点,垂直方向有780个像素点。分辨率高的显示屏可以显示更多细节，反之则粗糙。

设备独立像素(保证图像在不同设备上占比相同)

​	 ios:pt 

​	android:dp 

​		独立像素和像素关系: 	window.devicePixelRatio 

视口(viewport) 

​	pc端:视口大小就是整个浏览器大小(包括浏览器的上栏目等) 	

​			document.doucumentElement.clientHeight



##### Responsive Web Design Pattern

**Mostly Fluid**:

consists of a fluid grid. On large or medium screens, it usually remains the same size, simply adjusting the margins on wider screens. On smaller screens, the fluid grid causes the main content to reflow, while columns are stacked vertically. One major advantage of this pattern is that it usually only reuqires one breakpoint between small screens and large screens



**Column drop**:

For full-width multi-column layouts, column drop simply stacks teh columns vertically as the window becomes too narrows for the content.

Eventually this results in all of the columns being stacked vertically. Choosing breakpoints for this layout pattern is dependent on the content and chanegs for each design.

Content is stacked vertically in the smallest view, but as the screen expands beyond 600px, the parimary and secondary content `div`'s take the full width of the screen. The order of the `div`'s is set using the order CSS property. At 800px all three content `div`'s are shown, using the full width.

```css
.container {
  display: -webkit-flex;
  display: flex;
  -webkit-flex-flow: row wrap;
  flex-flow: row wrap;
}

.c1, .c2, .c3 {
  width: 100%;
}

@media (min-width: 600px) {
  .c1 {
    width: 60%;
    -webkit-order: 2;
    order: 2;
  }

  .c2 {
    width: 40%;
    -webkit-order: 1;
    order: 1;
  }

  .c3 {
    width: 100%;
    -webkit-order: 3;
    order: 3;
  }
}


@media (min-width: 800px) {
  .c2 {
    width: 20%;
  }

  .c3 {
    width: 20%;
  }
}
```

**Layout shifter**:

The layout shifter pattern is the most responsive pattern, with multiple breakpoints across several screen widths.

Key to this layout is the way content moves about, instead of reflowing and dropping below other columns. Due to the significant differences between each major breakpoint, it is more complex to maintain and likely involves changes within elements, not just overall content layout.

```css
.container {
  display: -webkit-flex;
  display: flex;
  -webkit-flex-flow: row wrap;
  flex-flow: row wrap;
}

.c1, .c2, .c3, .c4 {
  width: 100%;
}

@media (min-width: 600px) {
  .c1 {
    width: 25%;
  }

  .c4 {
    width: 75%;
  }

}

@media (min-width: 800px) {
  .container {
    width: 800px;
    margin-left: auto;
    margin-right: auto;
  }
}
```

**Tiny tweaks**:

Tiny tweaks simply makes small changes to the layout, such as adjusting font size, resizing images, or moving content around in very minor ways.

It works well on single column layouts such as one page linear websites and text-heavy articles.

```css
.c1 {
  padding: 10px;
  width: 100%;
}

@media (min-width: 500px) {
  .c1 {
    padding: 20px;
    font-size: 1.5em;
  }
}

@media (min-width: 800px) {
  .c1 {
    padding: 40px;
    font-size: 2em;
  }
}
```



**Off canvas**:

Rather than stacking content vertically, the off canvas pattern places less frequently used content—perhaps navigation or app menus—off screen, only showing it when the screen size is large enough, and on smaller screens, content is only a click away.

Rather than stacking content vertically, this sample uses a `transform: translate(-250px, 0)` declaration to hide two of the content `div`s off screen. JavaScript is used to show the divs by adding an open class to the element to make visible. As the screen gets wider, the off-screen positioning is removed from the elements and they're shown within the visible viewport.

Note in this sample, Safari for iOS 6 and Android Browser do not support the `flex-flow: row nowrap` feature of `flexbox`, so we’ve had to fall back to absolute positioning.

```css
body {
  overflow-x: hidden;
}

.container {
  display: block;
}

.c1, .c3 {
  position: absolute;
  width: 250px;
  height: 100%;

  /*
    This is a trick to improve performance on newer versions of Chrome
    #perfmatters
  */
  -webkit-backface-visibility: hidden;
  backface-visibility: hidden; 

  -webkit-transition: -webkit-transform 0.4s ease-out;
  transition: transform 0.4s ease-out;

  z-index: 1;
}

.c1 {
  /*
  Using translate3d as a trick to improve performance on older versions of Chrome
  See: http://aerotwist.com/blog/on-translate3d-and-layer-creation-hacks/
  #perfmatters
  */
  -webkit-transform: translate(-250px,0);
  transform: translate(-250px,0);
}

.c2 {
  width: 100%;
  position: absolute;
}

.c3 {
  left: 100%;
}

.c1.open {
  -webkit-transform: translate(0,0);
  transform: translate(0,0);
}

.c3.open {
  -webkit-transform: translate(-250px,0);
  transform: translate(-250px,0);
}

@media (min-width: 500px) {
  /* If the screen is wider then 500px, use Flexbox */
  .container {
    display: -webkit-flex;
    display: flex;
    -webkit-flex-flow: row nowrap;
    flex-flow: row nowrap;
  }
  .c1 {
    position: relative;
    -webkit-transition: none 0s ease-out;
    transition: none 0s ease-out;
    -webkit-transform: translate(0,0);
    transform: translate(0,0);
  }
  .c2 {
    position: static;
  }
}

@media (min-width: 800px) {
  body {
    overflow-x: auto;
  }
  .c3 {
    position: relative;
    left: auto;
    -webkit-transition: none 0s ease-out;
    transition: none 0s ease-out;
    -webkit-transform: translate(0,0);
    transform: translate(0,0);
  }
}
```



#### Images

| Browser width | Device pixel ratio | Image used | Effective resolution |
| :------------ | :----------------- | :--------- | :------------------- |
| 400px         | 1                  | `200.jpg`  | 1x                   |
| 400px         | 2                  | `400.jpg`  | 2x                   |
| 320px         | 2                  | `400.jpg`  | 2.5x                 |
| 600px         | 2                  | `800.jpg`  | 2.67x                |
| 640px         | 3                  | `1000.jpg` | 3.125x               |
| 1100px        | 1                  | `800.png`  | 1.45x                |

**SVG**: SVG makes it possible to include responsive vector graphics in a web page. 

​	The main advanatge of vector file formats over raster file formats is that the browser can render a vector image at any size. 

 Vector formats describe the geometry of the image—how it's constructed from lines, curves, and colors and so on. Raster formats, on the other hand, only have information about individual dots of color, so the browser has to guess how to fill in the blanks when scaling.





##### 60-30-10 Color Rule

Width is 100%

60% of neutral color

30%: lighter color

10% ›› actionable color



 