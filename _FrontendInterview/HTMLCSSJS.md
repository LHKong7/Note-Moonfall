# Nowcoder Front-end 500 [https://www.nowcoder.com/ta/review-frontend/review?page=2]



https://juejin.cn/post/6850418118854967304#heading-36



[TOC]



##### 76. WebSocket的实现和应用

(1)什么是WebSocket?

WebSocket是HTML5中的协议，

WebSocket 支持持久连续，
http协议不支持持久性连接。Http1.0和HTTP1.1都不支持持久性的链接，HTTP1.1中的keep-alive，将多个http请求合并为1个 

(2)WebSocket是什么样的协议，具体有什么优点？

HTTP的生命周期通过Request来界定，也就是Request一个Response，那么在Http1.0协议中，这次Http请求就结束了。在Http1.1中进行了改进，是的有一个connection：Keep-alive，也就是说，在一个Http连接中，可以发送多个Request，接收多个Response。但是必须记住，在Http中一个Request只能对应有一个Response，而且这个Response是被动的，不能主动发起。

WebSocket是基于Http协议的，或者说借用了Http协议来完成一部分握手，在握手阶段与Http是相同的。我们来看一个websocket握手协议的实现，基本是2个属性，upgrade，connection。

基本请求如下：

```
GET /chat HTTP/1.1
Host: server.example.com
Upgrade: websocket
Connection: Upgrade
Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
Sec-WebSocket-Protocol: chat, superchat
Sec-WebSocket-Version: 13
Origin: http://example.com
```

多了下面2个属性：

```
Upgrade:webSocket
Connection:Upgrade
```

告诉服务器发送的是websocket

```
Sec-WebSocket-Key: x3JJHMbDL1EzLkh9GBhXDw==
Sec-WebSocket-Protocol: chat, superchat
Sec-WebSocket-Version: 13
```

##### 77. HTTP请求的方式，HEAD方式

head：类似于get请求，只不过返回的响应中没有具体的内容，用户获取报头

options：允许客户端查看服务器的性能，比如说服务器支持的请求方式等等。



##### 78. 一个图片url访问后直接下载怎样实现？

请求的返回头里面，用于浏览器解析的重要参数就是OSS的API文档里面的返回http头，决定用户下载行为的参数。

下载的情况下：

1. x-oss-object-type:Normal

2. x-oss-request-id:598D5ED34F29D01FE2925F41

3. x-oss-storage-class:Standard

##### 79. 说一下web Quality（无障碍）

能够被残障人士使用的网站才能称得上一个易用的（易访问的）网站。

残障人士指的是那些带有残疾或者身体不健康的用户。

使用alt属性：

`<img src="person.jpg"  alt="this is a person"/>`

有时候浏览器会无法显示图像。具体的原因有：

用户关闭了图像显示

浏览器是不支持图形显示的迷你浏览器

浏览器是语音浏览器（供盲人和弱视人群使用）
如果您使用了alt 属性，那么浏览器至少可以显示或读出有关图像的描述。

##### 80. 几个很实用的BOM属性对象方法?

什么是Bom? Bom是浏览器对象。有哪些常用的Bom属性呢？

(1)location对象

location.href-- 返回或设置当前文档的URL
location.search -- 返回URL中的查询字符串部分。例如 http://www.dreamdu.com/dreamdu.php?id=5&name=dreamdu 返回包括(?)后面的内容?id=5&name=dreamdu
location.hash -- 返回URL#后面的内容，如果没有#，返回空
location.host -- 返回URL中的域名部分，例如[www.dreamdu.com](http://www.dreamdu.com/)
location.hostname -- 返回URL中的主域名部分，例如dreamdu.com
location.pathname -- 返回URL的域名后的部分。例如 http://www.dreamdu.com/xhtml/ 返回/xhtml/
location.port -- 返回URL中的端口部分。例如 http://www.dreamdu.com:8080/xhtml/ 返回8080
location.protocol -- 返回URL中的协议部分。例如 http://www.dreamdu.com:8080/xhtml/ 返回(//)前面的内容http:
location.assign -- 设置当前文档的URL
location.replace() -- 设置当前文档的URL，并且在history对象的地址列表中移除这个URL location.replace(url);
location.reload() -- 重载当前页面

(2)history对象

history.go() -- 前进或后退指定的页面数 history.go(num);
history.back() -- 后退一页
history.forward() -- 前进一页

(3)Navigator对象

navigator.userAgent -- 返回用户代理头的字符串表示(就是包括浏览器版本信息等的字符串)
navigator.cookieEnabled -- 返回浏览器是否支持(启用)cookie

##### 81. 说一下HTML5 drag api

```
dragstart：事件主体是被拖放元素，在开始拖放被拖放元素时触发，。
darg：事件主体是被拖放元素，在正在拖放被拖放元素时触发。
dragenter：事件主体是目标元素，在被拖放元素进入某元素时触发。
dragover：事件主体是目标元素，在被拖放在某元素内移动时触发。
dragleave：事件主体是目标元素，在被拖放元素移出目标元素是触发。
drop：事件主体是目标元素，在目标元素完全接受被拖放元素时触发。
dragend：事件主体是被拖放元素，在整个拖放操作结束时触发
```



##### 82. 说一下http2.0

首先补充一下，http和https的区别，相比于http,https是基于ssl加密的http协议

简要概括：http2.0是基于1999年发布的http1.0之后的首次更新。

提升访问速度（可以对于，请求资源所需时间更少，访问速度更快，相比http1.0）

允许多路复用：多路复用允许同时通过单一的HTTP/2连接发送多重请求-响应信息。

​	改善了：在http1.1中，浏览器客户端在同一时间，针对同一域名下的请求有一定数量限制（连接数量），超过限制会被阻塞。

二进制分帧：HTTP2.0会将所有的传输信息分割为更小的信息或者帧，并对他们进行二进制编码

首部压缩

服务器端推送

##### 83. 补充400和401、403状态码

(1)400状态码：请求无效

产生原因：

前端提交数据的字段名称和字段类型与后台的实体没有保持一致

前端提交到后台的数据应该是json字符串类型，但是前端没有将对象JSON.stringify转化成字符串。

解决方法：

对照字段的名称，保持一致性

将obj对象通过JSON.stringify实现序列化

(2)401状态码：当前请求需要用户验证

(3)403状态码：服务器已经得到请求，但是拒绝执行



##### 84. fetch发送2次请求的原因

fetch发送post请求的时候，总是发送2次，第一次状态码是204，第二次才成功？

原因很简单，因为你用fetch的post请求的时候，导致fetch 第一次发送了一个Options请求，询问服务器是否支持修改的请求头，如果服务器支持，则在第二次中发送真正的请求

##### 85. Cookie、sessionStorage、localStorage的区别

共同点：都是保存在浏览器端，并且是同源的

Cookie：cookie数据始终在同源的http请求中携带（即使不需要），即cookie在浏览器和服务器间来回传递。而sessionStorage和localStorage不会自动把数据发给服务器，仅在本地保存。cookie数据还有路径（path）的概念，可以限制cookie只属于某个路径下,存储的大小很小只有4K左右。 （key：可以在浏览器和服务器端来回传递，存储容量小，只有大约4K左右）

sessionStorage：仅在当前浏览器窗口关闭前有效，自然也就不可能持久保持，localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie只在设置的cookie过期时间之前一直有效，即使窗口或浏览器关闭。（key：本身就是一个回话过程，关闭浏览器后消失，session为一个回话，当页面不同即使是同一页面打开两次，也被视为同一次回话）

localStorage：localStorage 在所有同源窗口中都是共享的；cookie也是在所有同源窗口中都是共享的。（key：同源窗口都会共享，并且不会失效，不管窗口或者浏览器关闭与否都会始终生效）

补充说明一下cookie的作用：

保存用户登录状态。例如将用户id存储于一个cookie内，这样当用户下次访问该页面时就不需要重新登录了，现在很多论坛和社区都提供这样的功能。 cookie还可以设置过期时间，当超过时间期限后，cookie就会自动消失。因此，系统往往可以提示用户保持登录状态的时间：常见选项有一个月、三个 月、一年等。

跟踪用户行为。例如一个天气预报网站，能够根据用户选择的地区显示当地的天气情况。如果每次都需要选择所在地是烦琐的，当利用了cookie后就会显得很人性化了，系统能够记住上一次访问的地区，当下次再打开该页面时，它就会自动显示上次用户所在地区的天气情况。因为一切都是在后 台完成，所以这样的页面就像为某个用户所定制的一样，使用起来非常方便定制页面。如果网站提供了换肤或更换布局的功能，那么可以使用cookie来记录用户的选项，例如：背景色、分辨率等。当用户下次访问时，仍然可以保存上一次访问的界面风格。

##### 86. 说一下web worker

在HTML页面中，如果在执行脚本时，页面的状态是不可相应的，直到脚本执行完成后，页面才变成可相应。web worker是运行在后台的js，独立于其他脚本，不会影响页面你的性能。并且通过postMessage将结果回传到主线程。这样在进行复杂操作的时候，就不会阻塞主线程了。

如何创建web worker：

检测浏览器对于web worker的支持性

创建web worker文件（js，回传函数等）

创建web worker对象



##### 87. 对HTML语义化标签的理解

HTML5语义化标签是指正确的标签包含了正确的内容，结构良好，便于阅读，比如nav表示导航条，类似的还有article、header、footer等等标签。

##### 88. iframe是什么？有什么缺点？

定义：iframe元素会创建包含另一个文档的内联框架

提示：可以将提示文字放在`<iframe></iframe>`之间，来提示某些不支持iframe的浏览器

缺点：

会阻塞主页面的onload事件

搜索引擎无法解读这种页面，不利于SEO

iframe和主页面共享连接池，而浏览器对相同区域有限制所以会影响性能。



##### 89. Doctype作用?严格模式与混杂模式如何区分？它们有何意义?

Doctype声明于文档最前面，告诉浏览器以何种方式来渲染页面，这里有两种模式，严格模式和混杂模式。

严格模式的排版和JS 运作模式是 以该浏览器支持的最高标准运行。

混杂模式，向后兼容，模拟老式浏览器，防止浏览器无法兼容页面。



##### 90. Cookie如何防范XSS攻击

XSS（跨站脚本攻击）是指攻击者在返回的HTML中嵌入javascript脚本，为了减轻这些攻击，需要在HTTP头部配上，

 set-cookie：

httponly-这个属性可以防止XSS,它会禁止javascript脚本来访问cookie。

secure - 这个属性告诉浏览器仅在请求为https的时候发送cookie。

结果应该是这样的：`Set-Cookie=<cookie-value>.....`



##### 91. Cookie和session的区别

HTTP是一个无状态协议，因此Cookie的最大的作用就是存储sessionId用来唯一标识用户



##### 92. 一句话概括RESTFUL

就是用URL定位资源，用HTTP描述操作

##### 93. 讲讲viewport和移动端布局



##### 94. click在ios上有300ms延迟，原因及如何解决？

(1)粗暴型，禁用缩放

<meta name="viewport" content="width=device-width, user-scalable=no">

(2)利用FastClick，其原理是：

检测到touchend事件后，立刻出发模拟click事件，并且把浏览器300毫秒之后真正出发的事件给阻断掉



##### 95. addEventListener参数

addEventListener(event, function, useCapture)

其中，event指定事件名；function指定要事件触发时执行的函数；useCapture指定事件是否在捕获或冒泡阶段执行



##### 96. cookie sessionStorage localStorage区别

cookie数据始终在同源的http请求中携带(即使不需要)，即cookie在浏览器和服务器间来回传递

cookie数据还有路径（path）的概念，可以限制。cookie只属于某个路径下

存储大小限制也不同，cookie数据不能超过4K，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据，如回话标识。

webStorage虽然也有存储大小的限制，但是比cookie大得多，可以达到5M或更大

数据的有效期不同sessionStorage：仅在当前的浏览器窗口关闭有效；localStorage：始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie：只在设置的cookie过期时间之前一直有效，即使窗口和浏览器关闭

作用域不同sessionStorage：不在不同的浏览器窗口中共享，即使是同一个页面；localStorage：在所有同源窗口都是共享的；cookie：也是在所有同源窗口中共享的



##### 97. cookie session区别

1. cookie数据存放在客户的浏览器上，session数据放在服务器上。

2. cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗
   考虑到安全应当使用session。

3. session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能
   考虑到减轻服务器性能方面，应当使用COOKIE。

4. 单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。



##### 98 iframe通信，同源和不同源两种情况，多少种方法。同源我说了，根据父页面以及cookie，不同源我说了设置子域的方法。



##### 99. 介绍知道的http返回的状态码

100  Continue  继续。客户端应继续其请求

101  Switching Protocols  切换协议。服务器根据客户端的请求切换协议。只能切换到更高级的协议，例如，切换到HTTP的新版本协议

200  OK  请求成功。一般用于GET与POST请求

201  Created  已创建。成功请求并创建了新的资源

202  Accepted  已接受。已经接受请求，但未处理完成

203  Non-Authoritative Information  非授权信息。请求成功。但返回的meta信息不在原始的服务器，而是一个副本

204  No Content  无内容。服务器成功处理，但未返回内容。在未更新网页的情况下，可确保浏览器继续显示当前文档

205  Reset Content  重置内容。服务器处理成功，用户终端（例如：浏览器）应重置文档视图。可通过此返回码清除浏览器的表单域

206  Partial Content  部分内容。服务器成功处理了部分GET请求

300  Multiple Choices  多种选择。请求的资源可包括多个位置，相应可返回一个资源特征与地址的列表用于用户终端（例如：浏览器）选择

301  Moved Permanently  永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI代替

302  Found  临时移动。与301类似。但资源只是临时被移动。客户端应继续使用原有URI

303  See Other  查看其它地址。与301类似。使用GET和POST请求查看

304  Not Modified  未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望只返回在指定日期之后修改的资源

305  Use Proxy  使用代理。所请求的资源必须通过代理访问

306  Unused  已经被废弃的HTTP状态码

307  Temporary Redirect  临时重定向。与302类似。使用GET请求重定向

400  Bad Request  客户端请求的语法错误，服务器无法理解

401  Unauthorized  请求要求用户的身份认证

402  Payment Required  保留，将来使用

403  Forbidden  服务器理解请求客户端的请求，但是拒绝执行此请求

404  Not Found  服务器无法根据客户端的请求找到资源（网页）。通过此代码，网站设计人员可设置"您所请求的资源无法找到"的个性页面

405  Method Not Allowed  客户端请求中的方法被禁止

406  Not Acceptable  服务器无法根据客户端请求的内容特性完成请求

407  Proxy Authentication Required  请求要求代理的身份认证，与401类似，但请求者应当使用代理进行授权

408  Request Time-out  服务器等待客户端发送的请求时间过长，超时

409  Conflict  服务器完成客户端的PUT请求是可能返回此代码，服务器处理请求时发生了冲突

410  Gone  客户端请求的资源已经不存在。410不同于404，如果资源以前有现在被永久删除了可使用410代码，网站设计人员可通过301代码指定资源的新位置

411  Length Required  服务器无法处理客户端发送的不带Content-Length的请求信息

412  Precondition Failed  客户端请求信息的先决条件错误

413  Request Entity Too Large  由于请求的实体过大，服务器无法处理，因此拒绝请求。为防止客户端的连续请求，服务器可能会关闭连接。如果只是服务器暂时无法处理，则会包含一个Retry-After的响应信息

414  Request-URI Too Large  请求的URI过长（URI通常为网址），服务器无法处理

415  Unsupported Media Type  服务器无法处理请求附带的媒体格式

416  Requested range not satisfiable  客户端请求的范围无效

417  Expectation Failed  服务器无法满足Expect的请求头信息

500  Internal Server Error  服务器内部错误，无法完成请求

501  Not Implemented  服务器不支持请求的功能，无法完成请求

502  Bad Gateway  作为网关或者代理工作的服务器尝试执行请求时，从远程服务器接收到了一个无效的响应

503  Service Unavailable  由于超载或系统维护，服务器暂时的无法处理客户端的请求。延时的长度可包含在服务器的Retry-After头信息中

504  Gateway Time-out  充当网关或代理的服务器，未及时从远端服务器获取请求

505  HTTP Version not supported  服务器不支持请求的HTTP协议的版本，无法完成处理



##### 100. http常用请求头

| 协议头              | 说明                                                         |
| ------------------- | ------------------------------------------------------------ |
| Accept              | 可接受的响应内容类型（Content-Types）。                      |
| Accept-Charset      | 可接受的字符集                                               |
| Accept-Encoding     | 可接受的响应内容的编码方式。                                 |
| Accept-Language     | 可接受的响应内容语言列表。                                   |
| Accept-Datetime     | 可接受的按照时间来表示的响应内容版本                         |
| Authorization       | 用于表示HTTP协议中需要认证资源的认证信息                     |
| Cache-Control       | 用来指定当前的请求/回复中的，是否使用缓存机制。              |
| Connection          | 客户端（浏览器）想要优先使用的连接类型                       |
| Cookie              | 由之前服务器通过Set-Cookie（见下文）设置的一个HTTP协议Cookie |
| Content-Length      | 以8进制表示的请求体的长度                                    |
| Content-MD5         | 请求体的内容的二进制 MD5 散列值（数字签名），以 Base64 编码的结果 |
| Content-Type        | 请求体的MIME类型 （用于POST和PUT请求中）                     |
| Date                | 发送该消息的日期和时间（以[RFC 7231](https://www.nowcoder.com/ta/review-frontend/review?page=100#section-7.1.1.1)中定义的"HTTP日期"格式来发送） |
| Expect              | 表示客户端要求服务器做出特定的行为                           |
| From                | 发起此请求的用户的邮件地址                                   |
| Host                | 表示服务器的域名以及服务器所监听的端口号。如果所请求的端口是对应的服务的标准端口（80），则端口号可以省略。 |
| If-Match            | 仅当客户端提供的实体与服务器上对应的实体相匹配时，才进行对应的操作。主要用于像 PUT 这样的方法中，仅当从用户上次更新某个资源后，该资源未被修改的情况下，才更新该资源。 |
| If-Modified-Since   | 允许在对应的资源未被修改的情况下返回304未修改                |
| If-None-Match       | 允许在对应的内容未被修改的情况下返回304未修改（ 304 Not Modified ），参考 超文本传输协议 的实体标记 |
| If-Range            | 如果该实体未被修改过，则向返回所缺少的那一个或多个部分。否则，返回整个新的实体 |
| If-Unmodified-Since | 仅当该实体自某个特定时间以来未被修改的情况下，才发送回应。   |
| Max-Forwards        | 限制该消息可被代理及网关转发的次数。                         |
| Origin              | 发起一个针对[跨域资源共享](http://itbilu.com/javascript/js/VkiXuUcC.html)的请求（该请求要求服务器在响应中加入一个Access-Control-Allow-Origin的消息头，表示访问控制所允许的来源）。 |
| Pragma              | 与具体的实现相关，这些字段可能在请求/回应链中的任何时候产生。 |
| Proxy-Authorization | 用于向代理进行认证的认证信息。                               |
| Range               | 表示请求某个实体的一部分，字节偏移以0开始。                  |
| Referer             | 表示浏览器所访问的前一个页面，可以认为是之前访问页面的链接将浏览器带到了当前页面。Referer其实是Referrer这个单词，但RFC制作标准时给拼错了，后来也就将错就错使用Referer了。 |
| TE                  | 浏览器预期接受的传输时的编码方式：可使用回应协议头Transfer-Encoding中的值（还可以使用"trailers"表示数据传输时的分块方式）用来表示浏览器希望在最后一个大小为0的块之后还接收到一些额外的字段。 |
| User-Agent          | 浏览器的身份标识字符串                                       |
| Upgrade             | 要求服务器升级到一个高版本协议。                             |
| Via                 | 告诉服务器，这个请求是由哪些代理发出的。                     |
| Warning             | 一个一般性的警告，表示在实体内容体中可能存在错误。           |



##### 101. 强，协商缓存

缓存分为两种：强缓存和协商缓存，根据响应的header内容来决定。

|          | 获取资源形式 | 状态码              | 发送请求到服务器                 |
| -------- | ------------ | ------------------- | -------------------------------- |
| 强缓存   | 从缓存取     | 200（from cache）   | 否，直接从缓存取                 |
| 协商缓存 | 从缓存取     | 304（not modified） | 是，通过服务器来告知缓存是否可用 |

强缓存相关字段有expires，cache-control。如果cache-control与expires同时存在的话，cache-control的优先级高于expires。

协商缓存相关字段有Last-Modified/If-Modified-Since，Etag/If-None-Match



##### 102. HTTP状态码说说你知道的



##### 103. 讲讲304

304：如果客户端发送了一个带条件的GET 请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个304状态码。



##### 104. 强缓存、协商缓存什么时候用哪个

因为服务器上的资源不是一直固定不变的，大多数情况下它会更新，这个时候如果我们还访问本地缓存，那么对用户来说，那就相当于资源没有更新，用户看到的还是旧的资源；所以我们希望服务器上的资源更新了浏览器就请求新的资源，没有更新就使用本地的缓存，以最大程度的减少因网络请求而产生的资源浪费。



##### 105. 前端优化

网络优化： 降低请求量，合并资源，减少HTTP请求数，DNS预解析，减少域名数，CDN分发

客户端优化（browser & mobile device）：

- 缓存
- 渲染



降低请求量：合并资源，减少HTTP 请求数，minify / gzip 压缩，webP，lazyLoad。

加快请求速度：预解析DNS，减少域名数，并行加载，CDN 分发。

缓存：HTTP 协议缓存请求，离线缓存 manifest，离线数据缓存localStorage。

渲染：JS/CSS优化，加载顺序，服务端渲染，pipeline。



##### 106. GET和POST的区别

get参数通过url传递，post放在request body中。

get请求在url中传递的参数是有长度限制的，而post没有。

get比post更不安全，因为参数直接暴露在url中，所以不能用来传递敏感信息。

get请求只能进行url编码，而post支持多种编码方式

get请求会浏览器主动cache，而post支持多种编码方式。

get请求参数会被完整保留在浏览历史记录里，而post中的参数不会被保留。

GET和POST本质上就是TCP链接，并无差别。但是由于HTTP的规定和浏览器/服务器的限制，导致他们在应用过程中体现出一些不同。

GET产生一个TCP数据包；POST产生两个TCP数据包。



#### 107. 301和302的区别

301 Moved Permanently 被请求的资源已永久移动到新位置，并且将来任何对此资源的引用都应该使用本响应返回的若干个URI之一。如果可能，拥有链接编辑功能的客户端应当自动把请求的地址修改为从服务器反馈回来的地址。除非额外指定，否则这个响应也是可缓存的。

302 Found 请求的资源现在临时从不同的URI响应请求。由于这样的重定向是临时的，客户端应当继续向原有地址发送以后的请求。只有在Cache-Control或Expires中进行了指定的情况下，这个响应才是可缓存的。

字面上的区别就是301是永久重定向，而302是临时重定向。

301比较常用的场景是使用域名跳转。302用来做临时跳转 比如未登陆的用户访问用户中心重定向到登录页面。



##### 108. HTTP支持的方法

`GET, POST, HEAD, OPTIONS, PUT, DELETE, TRACE, CONNECT`



#### 109. 如何画一个三角形

```
div {
  width:0px;
  height:0px;
  border-top:10px solid red;
  border-right:10px solid transparent;
  border-bottom:10px solid transparent;
  border-left:10px solid transparent;
}
```

##### 110. 状态码304和 200

状态码200：请求已成功，请求所希望的响应头或数据体将随此响应返回。即返回的数据为全量的数据，如果文件不通过GZIP压缩的话，文件是多大，则要有多大传输量。

状态码304：如果客户端发送了一个带条件的 GET 请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个状态码。即客户端和服务器端只需要传输很少的数据量来做文件的校验，如果文件没有修改过，则不需要返回全量的数据。



##### 111. 说一下浏览器缓存

缓存分为两种：强缓存和协商缓存，根据响应的header内容来决定。

强缓存相关字段有expires，cache-control。如果cache-control与expires同时存在的话，cache-control的优先级高于expires。

协商缓存相关字段有Last-Modified/If-Modified-Since，Etag/If-None-Match



##### 112. HTML5新增的元素

首先html5为了更好的实践web语义化，增加了header，footer，nav,aside,section等语义化标签，在表单方面，为了增强表单，为input增加了color，emial,data ,range等类型，在存储方面，提供了sessionStorage，localStorage,和离线存储，通过这些存储方式方便数据在客户端的存储和获取，在多媒体方面规定了音频和视频元素audio和vedio，另外还有地理定位，canvas画布，拖放，多线程编程的web worker和websocket协议

##### 113 在地址栏里输入一个URL,到这个页面呈现出来，中间会发生什么？

DNS解析

TCP连接

发送HTTP请求

服务器处理请求并返回HTTP报文

浏览器解析渲染页面

连接结束

输入url后，首先需要找到这个url域名的服务器ip,为了寻找这个ip，浏览器首先会寻找缓存，查看缓存中是否有记录，缓存的查找记录为：浏览器缓存-》系统缓存-》路由器缓存，缓存中没有则查找系统的hosts文件中是否有记录，如果没有则查询DNS服务器，得到服务器的ip地址后，浏览器根据这个ip以及相应的端口号，构造一个http请求，这个请求报文会包括这次请求的信息，主要是请求方法，请求说明和请求附带的数据，并将这个http请求封装在一个tcp包中，这个tcp包会依次经过传输层，网络层，数据链路层，物理层到达服务器，服务器解析这个请求来作出响应，返回相应的html给浏览器，因为html是一个树形结构，浏览器根据这个html来构建DOM树，在dom树的构建过程中如果遇到JS脚本和外部JS连接，则会停止构建DOM树来执行和下载相应的代码，这会造成阻塞，这就是为什么推荐JS代码应该放在html代码的后面，之后根据外部央视，内部央视，内联样式构建一个CSS对象模型树CSSOM树，构建完成后和DOM树合并为渲染树，这里主要做的是排除非视觉节点，比如script，meta标签和排除display为none的节点，之后进行布局，布局主要是确定各个元素的位置和尺寸，之后是渲染页面，因为html文件中会含有图片，视频，音频等资源，在解析DOM的过程中，遇到这些都会进行并行下载，浏览器对每个域的并行下载数量有一定的限制，一般是4-6个，当然在这些所有的请求中我们还需要关注的就是缓存，缓存一般通过Cache-Control、Last-Modify、Expires等首部字段控制。 Cache-Control和Expires的区别在于Cache-Control使用相对时间，Expires使用的是基于服务器 端的绝对时间，因为存在时差问题，一般采用Cache-Control，在请求这些有设置了缓存的数据时，会先 查看是否过期，如果没有过期则直接使用本地缓存，过期则请求并在服务器校验文件是否修改，如果上一次 响应设置了ETag值会在这次请求的时候作为If-None-Match的值交给服务器校验，如果一致，继续校验 Last-Modified，没有设置ETag则直接验证Last-Modified，再决定是否返回304



##### 114. cookie和session的区别，localstorage和sessionstorage的区别

Cookie和session都可用来存储用户信息，cookie存放于客户端，session存放于服务器端，因为cookie存放于客户端有可能被窃取，所以cookie一般用来存放不敏感的信息，比如用户设置的网站主题，敏感的信息用session存储，比如用户的登陆信息，session可以存放于文件，数据库，内存中都可以，cookie可以服务器端响应的时候设置，也可以客户端通过JS设置cookie会在请求时在http首部发送给客户端，cookie一般在客户端有大小限制，一般为4K，

下面从几个方向区分一下cookie，localstorage，sessionstorage的区别

1、生命周期：

Cookie：可设置失效时间，否则默认为关闭浏览器后失效

Localstorage:除非被手动清除，否则永久保存

Sessionstorage：仅在当前网页会话下有效，关闭页面或浏览器后就会被清除

2、存放数据：

Cookie：4k左右

Localstorage和sessionstorage：可以保存5M的信息

3、http请求：

Cookie：每次都会携带在http头中，如果使用cookie保存过多数据会带来性能问题

其他两个：仅在客户端即浏览器中保存，不参与和服务器的通信

4、易用性：

Cookie：需要程序员自己封装，原生的cookie接口不友好

其他两个：即可采用原生接口，亦可再次封装

5、应用场景：

从安全性来说，因为每次http请求都回携带cookie信息，这样子浪费了带宽，所以cookie应该尽可能的少用，此外cookie还需要指定作用域，不可以跨域调用，限制很多，但是用户识别用户登陆来说，cookie还是比storage好用，其他情况下可以用storage，localstorage可以用来在页面传递参数，sessionstorage可以用来保存一些临时的数据，防止用户刷新页面后丢失了一些参数，



##### 115. 常见的HTTP的头部

可以将http首部分为通用首部，请求首部，响应首部，实体首部

通用首部表示一些通用信息，比如date表示报文创建时间，

请求首部就是请求报文中独有的，如cookie，和缓存相关的如if-Modified-Since

响应首部就是响应报文中独有的，如set-cookie，和重定向相关的location，

实体首部用来描述实体部分，如allow用来描述可执行的请求方法，content-type描述主题类型，content-Encoding描述主体的编码方式



##### 116. HTTP2.0 的特性

http2.0的特性如下：

1、内容安全，应为http2.0是基于https的，天然具有安全特性，通过http2.0的特性可以避免单纯使用https的性能下降

2、二进制格式，http1.X的解析是基于文本的，http2.0将所有的传输信息分割为更小的消息和帧，并对他们采用二进制格式编码，基于二进制可以让协议有更多的扩展性，比如引入了帧来传输数据和指令

3、多路复用，这个功能相当于是长连接的增强，每个request请求可以随机的混杂在一起，接收方可以根据request的id将request再归属到各自不同的服务端请求里面，另外多路复用中也支持了流的优先级，允许客户端告诉服务器那些内容是更优先级的资源，可以优先传输，

##### 117. cache-control的值有哪些

cache-control是一个通用消息头字段被用于HTTP请求和响应中，通过指定指令来实现缓存机制，这个缓存指令是单向的，常见的取值有private、no-cache、max-age、must-revalidate等，默认为private。

##### 118. 浏览器在生成页面的时候，会生成那两颗树？

构造两棵树，DOM树和CSSOM规则树

当浏览器接收到服务器相应来的HTML文档后，会遍历文档节点，生成DOM树，

CSSOM规则树由浏览器解析CSS文件生成，



##### 119. csrf和xss的网络攻击及防范

CSRF：跨站请求伪造，可以理解为攻击者盗用了用户的身份，以用户的名义发送了恶意请求，比如用户登录了一个网站后，立刻在另一个ｔａｂ页面访问量攻击者用来制造攻击的网站，这个网站要求访问刚刚登陆的网站，并发送了一个恶意请求，这时候CSRF就产生了，比如这个制造攻击的网站使用一张图片，但是这种图片的链接却是可以修改数据库的，这时候攻击者就可以以用户的名义操作这个数据库，防御方式的话：使用验证码，检查https头部的refer，使用token

XSS：跨站脚本攻击，是说攻击者通过注入恶意的脚本，在用户浏览网页的时候进行攻击，比如获取cookie，或者其他用户身份信息，可以分为存储型和反射型，存储型是攻击者输入一些数据并且存储到了数据库中，其他浏览者看到的时候进行攻击，反射型的话不存储在数据库中，往往表现为将攻击代码放在url地址的请求参数中，防御的话为cookie设置httpOnly属性，对用户的输入进行检查，进行特殊字符过滤



##### 120. 怎么看网站的性能如何

检测页面加载时间一般有两种方式，一种是被动去测：就是在被检测的页面置入脚本或探针，当用户访问网页时，探针自动采集数据并传回数据库进行分析，另一种主动监测的方式，即主动的搭建分布式受控环境，模拟用户发起页面访问请求，主动采集性能数据并分析，在检测的精准度上，专业的第三方工具效果更佳，比如说性能极客



##### 121. 介绍HTTP协议(特征)

HTTP是一个基于TCP/IP通信协议来传递数据（HTML 文件, 图片文件, 查询结果等）HTTP是一个属于应用层的面向对象的协议，由于其简捷、快速的方式，适用于分布式超媒体信息系统。它于1990年提出，经过几年的使用与发展，得到不断地完善和扩展。目前在WWW中使用的是HTTP/1.0的第六版，HTTP/1.1的规范化工作正在进行之中，而且HTTP-NG(Next Generation of HTTP)的建议已经提出。HTTP协议工作于客户端-服务端架构为上。浏览器作为HTTP客户端通过URL向HTTP服务端即WEB服务器发送所有请求。Web服务器根据接收到的请求后，向客户端发送响应信息。



##### 122. 输入URL到页面加载显示完成发生了什么?

DNS解析

TCP连接

发送HTTP请求

服务器处理请求并返回HTTP报文

浏览器解析渲染页面

连接结束



##### 123. 说一下对Cookie和Session的认知，Cookie有哪些限制？

\1.  cookie数据存放在客户的浏览器上，session数据放在服务器上。

\2.  cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗
考虑到安全应当使用session。

\3.  session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能
考虑到减轻服务器性能方面，应当使用COOKIE。

\4.  单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。



##### 124. 描述一下XSS和CRSF攻击？防御方法？

XSS, 即为（Cross Site Scripting）, 中文名为跨站脚本, 是发生在目标用户的浏览器层面上的，当渲染DOM树的过程成发生了不在预期内执行的JS代码时，就发生了XSS攻击。大多数XSS攻击的主要方式是嵌入一段远程或者第三方域上的JS代码。实际上是在目标网站的作用域下执行了这段js代码。

CSRF（Cross Site Request Forgery，跨站请求伪造），字面理解意思就是在别的站点伪造了一个请求。专业术语来说就是在受害者访问一个网站时，其 Cookie 还没有过期的情况下，攻击者伪造一个链接地址发送受害者并欺骗让其点击，从而形成 CSRF 攻击。

XSS防御的总体思路是：对输入(和URL参数)进行过滤，对输出进行编码。也就是对提交的所有内容进行过滤，对url中的参数进行过滤，过滤掉会导致脚本执行的相关内容；然后对动态输出到页面的内容进行html编码，使脚本无法在浏览器中执行。虽然对输入过滤可以被绕过，但是也还是会拦截很大一部分的XSS攻击。

防御CSRF 攻击主要有三种策略：验证 HTTP Referer 字段；在请求地址中添加 token 并验证；在 HTTP 头中自定义属性并验证。



##### 125. 知道304吗，什么时候用304？

304：如果客户端发送了一个带条件的GET 请求且该请求已被允许，而文档的内容（自上次访问以来或者根据请求的条件）并没有改变，则服务器应当返回这个304状态码。



##### 126. 具体有哪些请求头是跟缓存相关的

缓存分为两种：强缓存和协商缓存，根据响应的header内容来决定。

强缓存相关字段有expires，cache-control。如果cache-control与expires同时存在的话，cache-control的优先级高于expires。

协商缓存相关字段有Last-Modified/If-Modified-Since，Etag/If-None-Match



##### 127. cookie和session的区别

\1.  cookie数据存放在客户的浏览器上，session数据放在服务器上。

\2.  cookie不是很安全，别人可以分析存放在本地的COOKIE并进行COOKIE欺骗
考虑到安全应当使用session。

\3.  session会在一定时间内保存在服务器上。当访问增多，会比较占用你服务器的性能
考虑到减轻服务器性能方面，应当使用COOKIE。

\4.  单个cookie保存的数据不能超过4K，很多浏览器都限制一个站点最多保存20个cookie。

##### 128. cookie有哪些字段可以设置

name字段为一个cookie的名称。

value字段为一个cookie的值。

domain字段为可以访问此cookie的域名。

非顶级域名，如二级域名或者三级域名，设置的cookie的domain只能为顶级域名或者二级域名或者三级域名本身，不能设置其他二级域名的cookie，否则cookie无法生成。

顶级域名只能设置domain为顶级域名，不能设置为二级域名或者三级域名，否则cookie无法生成。

二级域名能读取设置了domain为顶级域名或者自身的cookie，不能读取其他二级域名domain的cookie。所以要想cookie在多个二级域名中共享，需要设置domain为顶级域名，这样就可以在所有二级域名里面或者到这个cookie的值了。
顶级域名只能获取到domain设置为顶级域名的cookie，其他domain设置为二级域名的无法获取。

path字段为可以访问此cookie的页面路径。 比如domain是abc.com,path是/test，那么只有/test路径下的页面可以读取此cookie。

expires/Max-Age 字段为此cookie超时时间。若设置其值为一个时间，那么当到达此时间后，此cookie失效。不设置的话默认值是Session，意思是cookie会和session一起失效。当浏览器关闭(不是浏览器标签页，而是整个浏览器) 后，此cookie失效。

Size字段 此cookie大小。

http字段  cookie的httponly属性。若此属性为true，则只有在http请求头中会带有此cookie的信息，而不能通过document.cookie来访问此cookie。

secure 字段 设置是否只能通过https来传递此条cookie

##### 129. cookie有哪些编码方式？

`encodeURI（）`

##### 130. 前端优化策略



##### 131. 既然你看过图解http，那你回答下200和304的区别

200  OK  请求成功。一般用于GET与POST请求

304  Not Modified  未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望只返回在指定日期之后修改的资源



##### 132. 除了cookie，还有什么存储方式。说说cookie和localStorage的区别

还有localStorage，sessionStorage，indexdDB等

cookie和localStorage的区别：

cookie数据始终在同源的http请求中携带(即使不需要)，即cookie在浏览器和服务器间来回传递

cookie数据还有路径（path）的概念，可以限制。cookie只属于某个路径下

存储大小限制也不同，cookie数据不能超过4K，同时因为每次http请求都会携带cookie，所以cookie只适合保存很小的数据，如回话标识。

localStorage虽然也有存储大小的限制，但是比cookie大得多，可以达到5M或更大

localStorage始终有效，窗口或浏览器关闭也一直保存，因此用作持久数据；cookie只在设置的cookie过期时间之前一直有效，即使窗口和浏览器关闭。



##### 133. 浏览器输入网址到页面渲染全过程

DNS解析

TCP连接

发送HTTP请求

服务器处理请求并返回HTTP报文

浏览器解析渲染页面

连接结束



##### 134. HTML5和CSS3用的多吗？你了解它们的新属性吗？有在项目中用过吗？

html5：

1）标签增删

8个语义元素 header section footer aside nav main article figure

内容元素mark高亮 progress进度

新的表单控件calander date time email url search

新的input类型 color date datetime datetime-local email

移除过时标签big font frame frameset

2）canvas绘图，支持内联SVG。支持MathML

3）多媒体audio video source embed track

4）本地离线存储，把需要离线存储在本地的文件列在一个manifest配置文件

5）web存储。localStorage、SessionStorage



css3：

CSS3边框如border-radius，box-shadow等；CSS3背景如background-size，background-origin等；CSS3 2D，3D转换如transform等；CSS3动画如animation等。 参考https://www.cnblogs.com/xkweb/p/5862612.html



##### 135. HTTP状态码



##### 136. http常见的请求方法

get、post，这两个用的是最多的，还有很多比如patch、delete、put、options等等



##### 137. get和post的区别

GET - 从指定的资源请求数据。

POST - 向指定的资源提交要被处理的数据。

GET：不同的浏览器和服务器不同，一般限制在2~8K之间，更加常见的是1k以内。

GET和POST的底层也是TCP/IP，GET/POST都是TCP链接。

GET产生一个TCP数据包；POST产生两个TCP数据包。

对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；

而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。

##### 138. 说说302，301，304的状态码

301  Moved Permanently  永久移动。请求的资源已被永久的移动到新URI，返回信息会包括新的URI，浏览器会自动定向到新URI。今后任何新的请求都应使用新的URI代替

302  Found  临时移动。与301类似。但资源只是临时被移动。客户端应继续使用原有URI

304  Not Modified  未修改。所请求的资源未修改，服务器返回此状态码时，不会返回任何资源。客户端通常会缓存访问过的资源，通过提供一个头信息指出客户端希望只返回在指定日期之后修改的资



##### 139. web性能优化

降低请求量：合并资源，减少HTTP 请求数，minify / gzip 压缩，webP，lazyLoad。

加快请求速度：预解析DNS，减少域名数，并行加载，CDN 分发。

缓存：HTTP 协议缓存请求，离线缓存 manifest，离线数据缓存localStorage。

渲染：JS/CSS优化，加载顺序，服务端渲染，pipeline。



##### 140. 浏览器缓存机制

缓存分为两种：强缓存和协商缓存，根据响应的header内容来决定。

强缓存相关字段有expires，cache-control。如果cache-control与expires同时存在的话，cache-control的优先级高于expires。

协商缓存相关字段有Last-Modified/If-Modified-Since，Etag/If-None-Match



##### 141. post和get区别

GET - 从指定的资源请求数据。

POST - 向指定的资源提交要被处理的数据。

GET：不同的浏览器和服务器不同，一般限制在2~8K之间，更加常见的是1k以内。

GET和POST的底层也是TCP/IP，GET/POST都是TCP链接。

GET产生一个TCP数据包；POST产生两个TCP数据包。

对于GET方式的请求，浏览器会把http header和data一并发送出去，服务器响应200（返回数据）；

而对于POST，浏览器先发送header，服务器响应100 continue，浏览器再发送data，服务器响应200 ok（返回数据）。



##### 142. 说一下css盒模型

简介：就是用来装页面上的元素的矩形区域。CSS中的盒子模型包括IE盒子模型和标准的W3C盒子模型。

内容(content)、填充(padding)、边框(border)、边界(margin)， CSS盒子模式都具备这些属性。

box-sizing(有3个值哦)：border-box,padding-box,content-box.

**IE盒模型:width(宽度）= padding(内边距) + border(边框）+content(内容宽度）**

**W3C盒模型:width(宽度）=content(内容宽度）**



在CSS3中引入了box-sizing属性，

​	`box-sizing: content-box;` 表示标准的盒子模型

​	`box-sizing: border-box; `表示的是IE盒子模型

最后，前面我们还提到了，`box-sizing:padding-box` 这个属性值的宽度包含了左右padding+width

在ie盒模型中，比如我们设置width:200px，border:10px，padding: 10px,那么content就剩下180px了。

**JS如何设置获取盒模型对应的宽高**:

​	**方式一：document.style.width/height**

​	**方式二：document.currentStyle.width/height**

​	**方式三：window.getComputedStyle(dom).width/height**

​	**方式四：dom.getBoundingClientRect()**

​	**方式五、CSS外边距重叠引出BFC(格式化上下文)**



**BFC概念：块级格式上下文**

**如何创建BFC**

（1）float不为none

（2）position不为static或relative

（3）display为inline-block或是table相关

（4）overflow不为visible

**BFC的使用场景**

（1）解决垂直方向的边距重叠

（2）清除浮动

（3）不与浮动元素重叠





##### 143.  画一条0.5px的线

采用meta viewport的方式

<meta name="viewport" content="initial-scale=1.0, maximum-scale=1.0, user-scalable=no" />

采用border-image的方式

采用transform: scale()的方式



##### 144. link标签和import标签的区别

link属于html标签，而@import是css提供的

页面被加载时，link会同时被加载，而@import引用的css会等到页面加载结束后加载。

link是html标签，因此没有兼容性，而@import只有IE5以上才能识别。

link方式样式的权重高于@import的。



##### 145. transition和animation的区别

Animation和transition大部分属性是相同的，他们都是随时间改变元素的属性值，他们的主要区别是transition需要触发一个事件才能改变属性，而animation不需要触发任何事件的情况下才会随时间改变属性值，并且transition为2帧，从from .... to，而animation可以一帧一帧的。

##### 146 Flex布局

Flex是Flexible Box的缩写，意为"弹性布局"，用来为盒状模型提供最大的灵活性。
布局的传统解决方案，基于盒状模型，依赖display属性 + position属性 + float属性。它对于那些特殊布局非常不方便，比如，垂直居中就不容易实现。

简单的分为容器属性和元素属性
容器的属性：

flex-direction：决定主轴的方向（即子item的排列方法）
.box {
flex-direction: row | row-reverse | column | column-reverse;
}

flex-wrap：决定换行规则
.box{
flex-wrap: nowrap | wrap | wrap-reverse;
}

flex-flow：
.box {
flex-flow: <flex-direction> || <flex-wrap>;
}

justify-content：对其方式，水平主轴对齐方式

align-items：对齐方式，竖直轴线方向

项目的属性（元素的属性）：

order属性：定义项目的排列顺序，顺序越小，排列越靠前，默认为0

flex-grow属性：定义项目的放大比例，即使存在空间，也不会放大

flex-shrink属性：定义了项目的缩小比例，当空间不足的情况下会等比例的缩小，如果定义个item的flow-shrink为0，则为不缩小

flex-basis属性：定义了在分配多余的空间，项目占据的空间。

flex：是flex-grow和flex-shrink、flex-basis的简写，默认值为0 1 auto。

align-self：允许单个项目与其他项目不一样的对齐方式，可以覆盖align-items，默认属性为auto，表示继承父元素的align-items

比如说，用flex实现圣杯布局



##### 147. BFC（块级格式化上下文，用于清楚浮动，防止margin重叠等）

直译成：块级格式化上下文，是一个独立的渲染区域，并且有一定的布局规则。

BFC区域不会与float box重叠

BFC是页面上的一个独立容器，子元素不会影响到外面

计算BFC的高度时，浮动元素也会参与计算

那些元素会生成BFC：

根元素

float不为none的元素

position为fixed和absolute的元素

display为inline-block、table-cell、table-caption，flex，inline-flex的元素

overflow不为visible的元素



##### 148. 垂直居中的方法

1. margin:auto法

   ```
   div{
     width: 400px;
     height: 400px;
     position: relative;
     border: 1px solid #465468;
   }
   img{
     position: absolute;
     margin: auto;
     top: 0;
     left: 0;
     right: 0;
     bottom: 0;
   }
   html:
   <div>
     <img src="mm.jpg">
   </div>
   ```

   定位为上下左右为0，margin：0可以实现脱离文档流的居中.

2. margin负值法

   ```
   .container{
     width: 500px;
     height: 400px;
     border: 2px solid #379;
     position: relative;
   }
   .inner{
     width: 480px;
     height: 380px;
     background-color: #746;
     position: absolute;
     top: 50%;
     left: 50%;
     margin-top: -190px; /*height的一半*/
     margin-left: -240px; /*width的一半*/
   }
   ```

   

   

   

3. table-cell（未脱离文档流的）

   ```
   div{
   width: 300px;
   height: 300px;
   border: 3px solid #555;
   display: table-cell;
   vertical-align: middle;
   text-align: center;
   }
   img{
   vertical-align: middle;
   }
   ```

4. 利用flex

   将父元素设置为display:flex，并且设置align-items:center;justify-content:center;

   ```
   .container{
     width: 300px;
     height: 200px;
     border: 3px solid #546461;
     display: -webkit-flex;
     display: flex;
     -webkit-align-items: center;
     align-items: center;
     -webkit-justify-content: center;
     justify-content: center;
   }
   .inner{
     border: 3px solid #458761;
     padding: 20px;
   }
   ```



##### 149. 关于js动画和css3动画的差异性

渲染线程分为main thread和compositor thread，如果css动画只改变transform和opacity，这时整个CSS动画得以在compositor trhead完成（而js动画则会在main thread执行，然后出发compositor thread进行下一步操作），特别注意的是如果改变transform和opacity是不会layout或者paint的。

区别：

功能涵盖面，js比css大

实现/重构难度不一，CSS3比js更加简单，性能跳优方向固定

对帧速表现不好的低版本浏览器，css3可以做到自然降级

css动画有天然事件支持

css3有兼容性问题



##### 150. 说一下块元素和行元素

块元素：独占一行，并且有自动填满父元素，可以设置margin和pading以及高度和宽度

行元素：不会独占一行，width和height会失效，并且在垂直方向的padding和margin会失效。



##### 151. 多行元素的文本省略号

```
display: -webkit-box
-webkit-box-orient:vertical
-webkit-line-clamp:3
overflow:hidden
```

##### 152. visibility=hidden, opacity=0，display:none

opacity=0，该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定一些事件，如click事件，那么点击该区域，也能触发点击事件的

visibility=hidden，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已经绑定的事件

display=none，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素删除掉一样。



##### 153. 双边距重叠问题（外边距折叠）

多个相邻（兄弟或者父子关系）普通流的块元素垂直方向marigin会重叠

折叠的结果为：

两个相邻的外边距都是正数时，折叠结果是它们两者之间较大的值。
两个相邻的外边距都是负数时，折叠结果是两者绝对值的较大值。
两个外边距一正一负时，折叠结果是两者的相加的和。



##### 154. position属性 比较

固定定位fixed：

元素的位置相对于浏览器窗口是固定位置，即使窗口是滚动的它也不会移动。Fixed定位使元素的位置与文档流无关，因此不占据空间。 Fixed定位的元素和其他元素重叠。

相对定位relative：

如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直或水平位置，让这个元素“相对于”它的起点进行移动。 在使用相对定位时，无论是否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。

绝对定位absolute：

绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于<html>。 absolute 定位使元素的位置与文档流无关，因此不占据空间。 absolute 定位的元素和其他元素重叠。

粘性定位sticky：

元素先按照普通文档流定位，然后相对于该元素在流中的flow root（BFC）和 containing block（最近的块级祖先元素）定位。而后，元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。

默认定位Static：

默认值。没有定位，元素出现在正常的流中（忽略top, bottom, left, right 或者 z-index 声明）。

inherit:

规定应该从父元素继承position 属性的值。



##### 155. 浮动清除

方法一：使用带clear属性的空元素

在浮动元素后使用一个空元素如<div class="clear"></div>，并在CSS中赋予.clear{clear:both;}属性即可清理浮动。亦可使用<br class="clear" />或<hr class="clear" />来进行清理。

方法二：使用CSS的overflow属性

给浮动元素的容器添加overflow:hidden;或overflow:auto;可以清除浮动，另外在 IE6 中还需要触发 hasLayout ，例如为父元素设置容器宽高或设置 zoom:1。

在添加overflow属性后，浮动元素又回到了容器层，把容器高度撑起，达到了清理浮动的效果。

方法三：给浮动的元素的容器添加浮动

给浮动元素的容器也添加上浮动属性即可清除内部浮动，但是这样会使其整体浮动，影响布局，不推荐使用。

方法四：使用邻接元素处理

什么都不做，给浮动元素后面的元素添加clear属性。

方法五：使用CSS的:after伪元素

结合:after 伪元素（注意这不是伪类，而是伪元素，代表一个元素之后最近的元素）和 IEhack ，可以完美兼容当前主流的各大浏览器，这里的 IEhack 指的是触发 hasLayout。

给浮动元素的容器添加一个clearfix的class，然后给这个class添加一个:after伪元素实现元素末尾添加一个看不见的块元素（Block element）清理浮动。



##### 156. css3新特性

CSS3边框如border-radius，box-shadow等；CSS3背景如background-size，background-origin等；CSS3 2D，3D转换如transform等；CSS3动画如animation等



##### 157. CSS选择器有哪些，优先级呢

id 选择器，class 选择器，标签选择器，伪元素选择器，伪类选择器等

同一元素引用了多个样式时，排在后面的样式属性的优先级高；

样式选择器的类型不同时，优先级顺序为：id 选择器 > class 选择器 > 标签选择器；

标签之间存在层级包含关系时，后代元素会继承祖先元素的样式。如果后代元素定义了与祖先元素相同的样式，则祖先元素的相同的样式属性会被覆盖。继承的样式的优先级比较低，至少比标签选择器的优先级低；

带有!important 标记的样式属性的优先级最高；

样式表的来源不同时，优先级顺序为：内联样式> 内部样式 > 外部样式 > 浏览器用户自定义样式 > 浏览器默认样式

##### 158. 清除浮动的方法，能讲讲吗

方法一：使用带clear属性的空元素

在浮动元素后使用一个空元素如<div class="clear"></div>，并在CSS中赋予.clear{clear:both;}属性即可清理浮动。亦可使用<br class="clear" />或<hr class="clear" />来进行清理。

方法二：使用CSS的overflow属性

给浮动元素的容器添加overflow:hidden;或overflow:auto;可以清除浮动，另外在 IE6 中还需要触发 hasLayout ，例如为父元素设置容器宽高或设置 zoom:1。

在添加overflow属性后，浮动元素又回到了容器层，把容器高度撑起，达到了清理浮动的效果。

方法三：给浮动的元素的容器添加浮动

给浮动元素的容器也添加上浮动属性即可清除内部浮动，但是这样会使其整体浮动，影响布局，不推荐使用。

方法四：使用邻接元素处理

什么都不做，给浮动元素后面的元素添加clear属性。

方法五：使用CSS的:after伪元素

结合:after 伪元素（注意这不是伪类，而是伪元素，代表一个元素之后最近的元素）和 IEhack ，可以完美兼容当前主流的各大浏览器，这里的 IEhack 指的是触发 hasLayout。

给浮动元素的容器添加一个clearfix的class，然后给这个class添加一个:after伪元素实现元素末尾添加一个看不见的块元素（Block element）清理浮动。



##### 159. 怎么样让一个元素消失，讲讲

display:none; visibility:hidden; opacity: 0; 等等



##### 160. 介绍一下盒模型

CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：边距，边框，填充，和实际内容。

标准盒模型：一个块的总宽度=width+margin(左右)+padding(左右)+border(左右)

怪异盒模型：一个块的总宽度=width+margin（左右）（既width已经包含了padding和border值）

设置盒模型：box-sizing:border-box



##### 161. position相关属性



##### 162. css动画如何实现

创建动画序列，需要使用animation属性或其子属性，该属性允许配置动画时间、时长以及其他动画细节，但该属性不能配置动画的实际表现，动画的实际表现是由 @keyframes规则实现，具体情况参见使用keyframes定义动画序列小节部分。

transition也可实现动画。transition强调过渡，是元素的一个或多个属性发生变化时产生的过渡效果，同一个元素通过两个不同的途径获取样式，而第二个途径当某种改变发生（例如hover）时才能获取样式，这样就会产生过渡动画。

##### 163. 如何实现图片在某个容器中居中的？

父元素固定宽高，利用定位及设置子元素margin值为自身的一半。

父元素固定宽高，子元素设置position: absolute，margin：auto平均分配margin

css3属性transform。子元素设置position: absolute; left: 50%; top: 50%;transform: translate(-50%,-50%);即可。

将父元素设置成display: table, 子元素设置为单元格 display: table-cell。

弹性布局display: flex。设置align-items: center; justify-content: center



##### 164. 如何实现元素的垂直居中

法一：父元素display:flex,align-items:center;

法二：元素绝对定位，top:50%，margin-top：-（高度/2）

法三：高度不确定用transform：translateY（-50%）

法四：父元素table布局，子元素设置vertical-align:center;



##### 165. CSS3中对溢出的处理

text-overflow属性，值为clip是修剪文本；ellipsis为显示省略符号来表被修剪的文本；string为使用给定的字符串来代表被修剪的文本。



##### 166. float的元素，display是什么

`display为block`



##### 167. 隐藏页面中某个元素的方法

display:none; visibility:hidden; opacity: 0; position移到外部，z-index涂层遮盖等等



##### 168. 三栏布局的实现方式，尽可能多写，浮动布局时，三个div的生成顺序有没有影响

三列布局又分为两种，两列定宽一列自适应，以及两侧定宽中间自适应

两列定宽一列自适应：

1、使用float+margin：

给div设置float：left，left的div添加属性margin-right：left和center的间隔px,right的div添加属性margin-left：left和center的宽度之和加上间隔

2、使用float+overflow：

给div设置float：left，再给right的div设置overflow:hidden。这样子两个盒子浮动，另一个盒子触发bfc达到自适应

3、使用position：

父级div设置position：relative，三个子级div设置position：absolute，这个要计算好盒子的宽度和间隔去设置位置，兼容性比较好，

4、使用table实现：

父级div设置display：table，设置border-spacing：10px//设置间距，取值随意,子级div设置display:table-cell，这种方法兼容性好，适用于高度宽度未知的情况，但是margin失效，设计间隔比较麻烦，

5、flex实现：

parent的div设置display：flex；left和center的div设置margin-right；然后right 的div设置flex：1；这样子right自适应，但是flex的兼容性不好

6、grid实现：

parent的div设置display：grid，设置grid-template-columns属性，固定第一列第二列宽度，第三列auto，

对于两侧定宽中间自适应的布局，对于这种布局需要把center放在前面，可以采用双飞翼布局：圣杯布局，来实现，也可以使用上述方法中的grid，table，flex，position实现



##### 169. 什么是BFC

BFC也就是常说的块格式化上下文，这是一个独立的渲染区域，规定了内部如何布局，并且这个区域的子元素不会影响到外面的元素，其中比较重要的布局规则有内部box垂直放置，计算BFC的高度的时候，浮动元素也参与计算，触发BFC的规则有根元素，浮动元素，position为absolute或fixed的元素，display为inline-block，table-cell，table-caption，flex，inline-flex，overflow不为visible的元素



##### 170. calc属性

Calc用户动态计算长度值，任何长度值都可以使用calc()函数计算，需要注意的是，运算符前后都需要保留一个空格，例如：width: calc(100% - 10px)；



##### 171. 有一个width300，height300，怎么实现在屏幕上垂直水平居中

对于行内块级元素，

1、父级元素设置text-alig：center，然后设置line-height和vertical-align使其垂直居中，最后设置font-size：0消除近似居中的bug

2、父级元素设置display：table-cell，vertical-align：middle达到水平垂直居中

3、采用绝对定位，原理是子绝父相，父元素设置position：relative，子元素设置position：absolute，然后通过transform或margin组合使用达到垂直居中效果，设置top：50%，left：50%，transform：translate（-50%，-50%）

4、绝对居中，原理是当top,bottom为0时，margin-top&bottom设置auto的话会无限延伸沾满空间并平分，当left，right为0时,margin-left&right设置auto会无限延伸占满空间并平分，

5、采用flex，父元素设置display：flex，子元素设置margin：auto

6、视窗居中，vh为视口单位，50vh即是视口高度的50/100，设置margin：50vh auto 0，transform：translate(-50%)



##### 172. display：table和本身的table有什么区别

Display:table和本身table是相对应的，区别在于，display：table的css声明能够让一个html元素和它的子节点像table元素一样，使用基于表格的css布局，是我们能够轻松定义一个单元格的边界，背景等样式，而不会产生因为使用了table那样的制表标签导致的语义化问题。

之所以现在逐渐淘汰了table系表格元素，是因为用div+css编写出来的文件比用table边写出来的文件小，而且table必须在页面完全加载后才显示，div则是逐行显示，table的嵌套性太多，没有div简洁



##### 173. position属性的值有哪些及其区别

Position属性把元素放置在一个静态的，相对的，绝对的，固定的位置中，

Static：位置设置为static的元素，他始终处于页面流给予的位置，static元素会忽略任何top,buttom,left,right声明

Relative：位置设置为relative的元素，可将其移至相对于其正常位置的地方，因此left：20会将元素移至元素正常位置左边20个像素的位置

Absolute：此元素可定位于相对包含他的元素的指定坐标，此元素可通过left，top等属性规定

Fixed：位置被设为fiexd的元素，可定为与相对浏览器窗口的指定坐标，可以通过left，top，right属性来定位



##### 174. z-index的定位方法

z-index属性设置元素的堆叠顺序，拥有更好堆叠顺序的元素会处于较低顺序元素之前，z-index可以为负，且z-index只能在定位元素上奏效，该属性设置一个定位元素沿z轴的位置，如果为正数，离用户越近，为负数，离用户越远，它的属性值有auto，默认，堆叠顺序与父元素相等，number，inherit，从父元素继承z-index属性的值



##### 175. CSS盒模型

##### 176. 如果想要改变一个DOM元素的字体颜色，不在它本身上进行操作？

可以更改父元素的color

##### 177. 对CSS的新属性有了解过的吗？

CSS3的新特性中，在布局方面新增了flex布局，在选择器方面新增了例如first-of-type,nth-child等选择器，在盒模型方面添加了box-sizing来改变盒模型，在动画方面增加了animation，2d变换，3d变换等，在颜色方面添加透明，rbga等，在字体方面允许嵌入字体和设置字体阴影，最后还有媒体查讯等



##### 178. 用的最多的css属性是啥？

用的目前来说最多的是flex属性，灵活但是兼容性方面不强，



##### 179. line-height和height的区别

line-height一般是指布局里面一段文字上下行之间的高度，是针对字体来设置的，height一般是指容器的整体高度，

##### 180. 设置一个元素的背景颜色，背景颜色会填充哪些区域？

background-color设置的背景颜色会填充元素的content、padding、border区域，



##### 181. 知道属性选择器和伪类选择器的优先级吗

属性选择器和伪类选择器优先级相同

##### 182. inline-block、inline和block的区别；为什么img是inline还可以设置宽高

Block是块级元素，其前后都会有换行符，能设置宽度，高度，margin/padding水平垂直方向都有效。

Inline：设置width和height无效，margin在竖直方向上无效，padding在水平方向垂直方向都有效，前后无换行符

Inline-block：能设置宽度高度，margin/padding水平垂直方向 都有效，前后无换行符

##### 183. 用css实现一个硬币旋转的效果





##### 184. 了解重绘和重排吗，知道怎么去减少重绘和重排吗，让文档脱离文档流有哪些方法

DOM的变化影响到了预算内宿的几何属性比如宽高，浏览器重新计算元素的几何属性，其他元素的几何属性也会受到影响，浏览器需要重新构造渲染书，这个过程称之为重排，

浏览器将受到影响的部分重新绘制在屏幕上 的过程称为重绘，

引起重排重绘的原因有：

- 添加或者删除可见的DOM元素，
- 元素尺寸位置的改变
- 浏览器页面初始化，
- 浏览器窗口大小发生改变，重排一定导致重绘，重绘不一定导致重排，

减少重绘重排的方法有：

- 不在布局信息改变时做DOM查询，
- 使用csstext,className一次性改变属性
- 使用fragment

对于多次重排的元素，比如说动画。使用绝对定位脱离文档流，使其不影响其他元素



##### 186. overflow的原理

要讲清楚这个解决方案的原理，首先需要了解块格式化上下文，A block formatting context is a part of a visual CSS rendering of a Web page. It is the region in which the layout of block boxes occurs and in which floats interact with each other.翻译过来就是块格式化上下文是CSS可视化渲染的一部分，它是一块区域，规定了内部块盒 的渲染方式，以及浮动相互之间的影响关系

当元素设置了overflow样式且值部位visible时，该元素就构建了一个BFC，BFC在计算高度时，内部浮动元素的高度也要计算在内，也就是说技术BFC区域内只有一个浮动元素，BFC的高度也不会发生塌缩，所以达到了清除浮动的目的，



##### 187. 清除浮动的方法

给要清除浮动的元素添加样式clear，\

父元素结束标签钱插入清除浮动的块级元素，给该元素添加样式clear

添加伪元素，在父级元素的最后，添加一个伪元素，通过清除伪元素的浮动，注意该伪元素的display为block，

父元素添加样式overflow清除浮动，overflow设置除visible以外的任何位置



##### 188. box-sizing的语法和基本用处

box-sizing规定两个并排的带边框的框，语法为box-sizing：content-box/border-box/inherit

content-box：宽度和高度分别应用到元素的内容框，在宽度和高度之外绘制元素的内边距和边框

border-box：为元素设定的宽度和高度决定了元素的边框盒，

inherit：继承父元素的box-sizing



##### 189. 使元素消失的方法有哪些？

1. opacity：0，该元素隐藏起来了，但不会改变页面布局，并且，如果该元素已经绑定一些事件，如click事件，那么点击该区域，也能触发点击事件的

2. visibility：hidden，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已经绑定的事件

3. display：none，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素删除掉。



##### 190. 两个嵌套的div，position都是absolute，子div设置top属性，那么这个top是相对于父元素的哪个位置定位的。

`border的内边缘`



##### 191. 说说盒子模型

CSS盒模型本质上是一个盒子，封装周围的HTML元素，它包括：边距，边框，填充，和实际内容。

标准盒模型：一个块的总宽度=width+margin(左右)+padding(左右)+border(左右)

怪异盒模型：一个块的总宽度=width+margin（左右）（既width已经包含了padding和border值）

如何设置：box-sizing:border-box



##### 192. display

主要取值有none,block,inline-block,inline,flex等。



##### 193. 怎么隐藏一个元素

##### 194. display:none和visibilty:hidden的区别

\1. visibility：hidden，该元素隐藏起来了，但不会改变页面布局，但是不会触发该元素已经绑定的事件

\2. display：none，把元素隐藏起来，并且会改变页面布局，可以理解成在页面中把该元素删除掉。



##### 195. 相对布局和绝对布局，position:relative和obsolute。

相对定位relative：

如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直或水平位置，让这个元素“相对于”它的起点进行移动。 在使用相对定位时，无论是否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。

绝对定位absolute：

绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于<html>。 absolute 定位使元素的位置与文档流无关，因此不占据空间。 absolute 定位的元素和其他元素重叠。



##### 196. flex布局



##### 197. block、inline、inline-block的区别。

block元素会独占一行，多个block元素会各自新起一行。默认情况下，block元素宽度自动填满其父元素宽度。

block元素可以设置width,height属性。块级元素即使设置了宽度,仍然是独占一行。

block元素可以设置margin和padding属性。

inline元素不会独占一行，多个相邻的行内元素会排列在同一行里，直到一行排列不下，才会新换一行，其宽度随元素的内容而变化。

inline元素设置width,height属性无效。

inline元素的margin和padding属性，水平方向的padding-left, padding-right, margin-left, margin-right都产生边距效果；但竖直方向的padding-top, padding-bottom, margin-top, margin-bottom不会产生边距效果。

inline-block：简单来说就是将对象呈现为inline对象，但是对象的内容作为block对象呈现。之后的内联对象会被排列在同一行内。比如我们可以给一个link（a元素）inline-block属性值，使其既具有block的宽度高度特性又具有inline的同行特性



##### 198. css的常用选择器

id选择器，类选择器，伪类选择器等



##### 199. css布局

六种布局方式总结：圣杯布局、双飞翼布局、Flex布局、绝对定位布局、表格布局、网格布局。

圣杯布局是指布局从上到下分为header、container、footer，然后container部分定为三栏布局。这种布局方式同样分为header、container、footer。圣杯布局的缺陷在于 center 是在 container 的padding中的，因此宽度小的时候会出现混乱。

双飞翼布局给center 部分包裹了一个 main 通过设置margin主动地把页面撑开。

Flex布局是由CSS3提供的一种方便的布局方式。

绝对定位布局是给container 设置position: relative和overflow: hidden，因为绝对定位的元素的参照物为第一个postion不为static的祖先元素。 left 向左浮动，right 向右浮动。center 使用绝对定位，通过设置left和right并把两边撑开。 center 设置top: 0和bottom: 0使其高度撑开。

表格布局的好处是能使三栏的高度统一。

网格布局可能是最强大的布局方式了，使用起来极其方便，但目前而言，兼容性并不好。网格布局，可以将页面分割成多个区域，或者用来定义内部元素的大小，位置，图层关系。



##### 200. css定位

固定定位fixed：

元素的位置相对于浏览器窗口是固定位置，即使窗口是滚动的它也不会移动。Fixed定位使元素的位置与文档流无关，因此不占据空间。 Fixed定位的元素和其他元素重叠。

相对定位relative：

如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直或水平位置，让这个元素“相对于”它的起点进行移动。 在使用相对定位时，无论是否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。

绝对定位absolute：

绝对定位的元素的位置相对于最近的已定位父元素，如果元素没有已定位的父元素，那么它的位置相对于<html>。 absolute 定位使元素的位置与文档流无关，因此不占据空间。 absolute 定位的元素和其他元素重叠。

粘性定位sticky：

元素先按照普通文档流定位，然后相对于该元素在流中的flow root（BFC）和 containing block（最近的块级祖先元素）定位。而后，元素定位表现为在跨越特定阈值前为相对定位，之后为固定定位。

默认定位Static：

默认值。没有定位，元素出现在正常的流中（忽略top, bottom, left, right 或者 z-index 声明）。

inherit:

规定应该从父元素继承position 属性的值。



##### 201. relative定位规则

如果对一个元素进行相对定位，它将出现在它所在的位置上。然后，可以通过设置垂直或水平位置，让这个元素“相对于”它的起点进行移动。 在使用相对定位时，无论是否进行移动，元素仍然占据原来的空间。因此，移动元素会导致它覆盖其它框。



##### 202. 垂直居中

父元素固定宽高，利用定位及设置子元素margin值为自身的一半。

父元素固定宽高，子元素设置position: absolute，margin：auto平均分配margin

css3属性transform。子元素设置position: absolute; left: 50%; top: 50%;transform: translate(-50%,-50%);即可。

将父元素设置成display: table, 子元素设置为单元格 display: table-cell。

弹性布局display: flex。设置align-items: center; justify-content: cen



##### 203. css预处理器有什么

less，sass等



##### 204. get请求传参长度的误区

误区：我们经常说get请求参数的大小存在限制，而post请求的参数大小是无限制的。

实际上HTTP 协议从未规定 GET/POST 的请求长度限制是多少。对get请求参数的限制是来源与浏览器或web服务器，浏览器或web服务器限制了url的长度。为了明确这个概念，我们必须再次强调下面几点:

HTTP 协议 未规定 GET 和POST的长度限制

GET的最大长度显示是因为 浏览器和 web服务器限制了 URI的长度

不同的浏览器和WEB服务器，限制的最大长度不一样

要支持IE，则最大长度为2083byte，若只支持Chrome，则最大长度 8182byte



##### 205 补充get和post请求在缓存方面的区别

post/get的请求区别，具体不再赘述。

补充补充一个get和post在缓存方面的区别：

get请求类似于查找的过程，用户获取数据，可以不用每次都与数据库连接，所以可以使用缓存。

post不同，post做的一般是修改和删除的工作，所以必须与数据库交互，所以不能使用缓存。因此get请求适合于请求缓存。

##### 206. 说一下闭包

一句话可以概括：闭包就是能够读取其他函数内部变量的函数，或者子函数在外调用，子函数所在的父函数的作用域不会被释放。



##### 207. 说一下类的创建和继承

1. 类的创建（es5）：new一个function，在这个function的prototype里面增加属性和方法。

2. 类的继承——原型链继承

   介绍：在这里我们可以看到new了一个空对象,这个空对象指向Animal并且Cat.prototype指向了这个空对象，这种就是基于原型链的继承。

   特点：基于原型链，既是父类的实例，也是子类的实例

   缺点：无法实现多继承

3. 构造继承：使用父类的构造函数来增强子类实例，等于是复制父类的实例属性给子类（没用到原型）

   ​	特点：可以实现多继承

   ​	缺点：只能继承父类实例的属性和方法，不能继承原型上的属性和方法。

4. 实例继承和拷贝继承

   实例继承：为父类实例添加新特性，作为子类实例返回

   拷贝继承：拷贝父类元素上的属性和方法

   上述两个实用性不强，不一一举例。

5. 组合继承：相当于构造继承和原型链继承的组合体。通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用

   特点：可以继承实例属性/方法，也可以继承原型属性/方法

   缺点：调用了两次父类构造函数，生成了两份实例

6. 寄生组合继承：通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性



##### 208. 如何解决异步回调地狱

`promise、generator、async/await`



##### 209. 说说前端中的事件流

HTML中与javascript交互是通过事件驱动来实现的，例如鼠标点击事件onclick、页面的滚动事件onscroll等等，可以向文档或者文档中的元素添加事件侦听器来预订事件。想要知道这些事件是在什么时候进行调用的，就需要了解一下“事件流”的概念。

什么是事件流：事件流描述的是从页面中接收事件的顺序,DOM2级事件流包括下面几个阶段。

事件捕获阶段

处于目标阶段

事件冒泡阶段

addEventListener：addEventListener 是DOM2 级事件新增的指定事件处理程序的操作，这个方法接收3个参数：要处理的事件名、作为事件处理程序的函数和一个布尔值。最后这个布尔值参数如果是true，表示在捕获阶段调用事件处理程序；如果是false，表示在冒泡阶段调用事件处理程序。

IE只支持事件冒泡。



##### 210. 如何让事件先冒泡后捕获

在DOM标准事件模型中，是先捕获后冒泡。但是如果要实现先冒泡后捕获的效果，对于同一个事件，监听捕获和冒泡，分别对应相应的处理函数，监听到捕获事件，先暂缓执行，直到冒泡事件被捕获后再执行捕获之间。



##### 211. 说一下事件委托

简介：事件委托指的是，不在事件的发生地（直接dom）上设置监听函数，而是在其父元素上设置监听函数，通过事件冒泡，父元素可以监听到子元素上事件的触发，通过判断事件发生元素DOM的类型，来做出不同的响应。

举例：最经典的就是ul和li标签的事件监听，比如我们在添加事件时候，采用事件委托机制，不会在li标签上直接添加，而是在ul父元素上添加。

好处：比较合适动态元素的绑定，新添加的子元素也会有监听函数，也可以有事件触发机制。



##### 212. 说一下图片的懒加载和预加载

预加载：提前加载图片，当用户需要查看时可直接从本地缓存中渲染。

懒加载：懒加载的主要目的是作为服务器前端的优化，减少请求数或延迟请求数。

两种技术的本质：两者的行为是相反的，一个是提前加载，一个是迟缓甚至不加载。
懒加载对服务器前端有一定的缓解压力作用，预加载则会增加服务器前端压力。



##### 213. mouseover和mouseenter的区别

mouseover：当鼠标移入元素或其子元素都会触发事件，所以有一个重复触发，冒泡的过程。对应的移除事件是mouseout

mouseenter：当鼠标移除元素本身（不包含元素的子元素）会触发事件，也就是不会冒泡，对应的移除事件是mouseleave



##### 214. js的new操作符做了哪些事情

new 操作符新建了一个空对象，这个对象原型指向构造函数的prototype，执行构造函数后返回这个对象。



###### 215. 改变函数内部this指针的指向函数（bind，apply，call的区别）

通过apply和call改变函数的this指向，他们两个函数的第一个参数都是一样的表示要改变指向的那个对象，第二个参数，apply是数组，而call则是arg1,arg2...这种形式。通过bind改变this作用域会返回一个新的函数，这个函数不会马上执行。



###### 216. js的各种位置，比如clientHeight,scrollHeight,offsetHeight ,以及scrollTop, offsetTop,clientTop的区别？

clientHeight：表示的是可视区域的高度，不包含border和滚动条

offsetHeight：表示可视区域的高度，包含了border和滚动条

scrollHeight：表示了所有区域的高度，包含了因为滚动被隐藏的部分。

clientTop：表示边框border的厚度，在未指定的情况下一般为0

scrollTop：滚动后被隐藏的高度，获取对象相对于由offsetParent属性指定的父坐标(css定位的元素或body元素)距离顶端的高度。



##### 217. js拖拽功能的实现

首先是三个事件，分别是mousedown，mousemove，mouseup

当鼠标点击按下的时候，需要一个tag标识此时已经按下，可以执行mousemove里面的具体方法。

clientX，clientY标识的是鼠标的坐标，分别标识横坐标和纵坐标，并且我们用offsetX和offsetY来表示元素的元素的初始坐标，移动的举例应该是：

鼠标移动时候的坐标-鼠标按下去时候的坐标。

也就是说定位信息为：

​	鼠标移动时候的坐标-鼠标按下去时候的坐标+元素初始情况下的offetLeft.

还有一点也是原理性的东西，也就是拖拽的同时是绝对定位，我们改变的是绝对定位条件下的left
以及top等等值。

补充：也可以通过html5的拖放（Drag 和 drop）来实现



##### 218. 异步加载js的方法

defer：只支持IE如果您的脚本不会改变文档的内容，可将 defer 属性加入到<script>标签中，以便加快处理文档的速度。因为浏览器知道它将能够安全地读取文档的剩余部分而不用执行脚本，它将推迟对脚本的解释，直到文档已经显示给用户为止。

async，HTML5属性仅适用于外部脚本，并且如果在IE中，同时存在defer和async，那么defer的优先级比较高，脚本将在页面完成时执行。

创建script标签，插入到DOM中



##### 219. Ajax解决浏览器缓存问题

在ajax发送请求前加上 anyAjaxObj.setRequestHeader("If-Modified-Since","0")。

在ajax发送请求前加上 anyAjaxObj.setRequestHeader("Cache-Control","no-cache")。

在URL后面加上一个随机数： "fresh=" + Math.random()。

在URL后面加上时间搓："nowtime=" + new Date().getTime()。

如果是使用jQuery，直接这样就可以了 $.ajaxSetup({cache:false})。这样页面的所有ajax都会执行这条语句就是不需要保存缓存记录。



##### 220. js的节流和防抖









##### 221. JS中的垃圾回收机制

必要性：由于字符串、对象和数组没有固定大小，所有当他们的大小已知时，才能对他们进行动态的存储分配。JavaScript程序每次创建字符串、数组或对象时，解释器都必须分配内存来存储那个实体。只要像这样动态地分配了内存，最终都要释放这些内存以便他们能够被再用，否则，JavaScript的解释器将会消耗完系统中所有可用的内存，造成系统崩溃。

这段话解释了为什么需要系统需要垃圾回收，JS不像C/C++，他有自己的一套垃圾回收机制（Garbage Collection）。JavaScript的解释器可以检测到何时程序不再使用一个对象了，当他确定了一个对象是无用的时候，他就知道不再需要这个对象，可以把它所占用的内存释放掉了。例如：

```
var a="hello world";
var b="world";
var a=b;
```

//这时，会释放掉"hello world"，释放内存以便再引用

垃圾回收的方法：标记清除、计数引用。

标记清除

这是最常见的垃圾回收方式，当变量进入环境时，就标记这个变量为”进入环境“,从逻辑上讲，永远不能释放进入环境的变量所占的内存，永远不能释放进入环境变量所占用的内存，只要执行流程进入相应的环境，就可能用到他们。当离开环境时，就标记为离开环境。

垃圾回收器在运行的时候会给存储在内存中的变量都加上标记（所有都加），然后去掉环境变量中的变量，以及被环境变量中的变量所引用的变量（条件性去除标记），删除所有被标记的变量，删除的变量无法在环境变量中被访问所以会被删除，最后垃圾回收器，完成了内存的清除工作，并回收他们所占用的内存。

引用计数法

另一种不太常见的方法就是引用计数法，引用计数法的意思就是每个值没引用的次数，当声明了一个变量，并用一个引用类型的值赋值给改变量，则这个值的引用次数为1,；相反的，如果包含了对这个值引用的变量又取得了另外一个值，则原先的引用值引用次数就减1，当这个值的引用次数为0的时候，说明没有办法再访问这个值了，因此就把所占的内存给回收进来，这样垃圾收集器再次运行的时候，就会释放引用次数为0的这些值。

用引用计数法会存在内存泄露，下面来看原因：

```
function problem() {
var objA = new Object();
var objB = new Object();
objA.someOtherObject = objB;
objB.anotherObject = objA;
}
```

在这个例子里面，objA和objB通过各自的属性相互引用，这样的话，两个对象的引用次数都为2，在采用引用计数的策略中，由于函数执行之后，这两个对象都离开了作用域，函数执行完成之后，因为计数不为0，这样的相互引用如果大量存在就会导致内存泄露。

特别是在DOM对象中，也容易存在这种问题：

```
var element=document.getElementById（’‘）；
var myObj=new Object();
myObj.element=element;
element.someObject=myObj;
```

这样就不会有垃圾回收的过程。

##### 220. js的节流和防抖

防抖（Debouncing）: 防抖技术即是可以把多个顺序地调用合并成一次，也就是在一定时间内，规定事件被触发的次数

节流（Throttling）: 防抖函数确实不错，但是也存在问题，譬如图片的懒加载，我希望在下滑过程中图片不断的被加载出来，而不是只有当我停止下滑时候，图片才被加载出来。又或者下滑时候的数据的 ajax 请求加载也是同理。



##### 222. eval是做什么的

它的功能是将对应的字符串解析成js并执行，应该避免使用js，因为非常消耗性能（2次，一次解析成js，一次执行）



##### 223. 如何理解前端模块化

前端模块化就是复杂的文件编程一个一个独立的模块，比如js文件等等，分成独立的模块有利于重用（复用性）和维护（版本迭代），这样会引来模块之间相互依赖的问题，所以有了commonJS规范，AMD，CMD规范等等，以及用于js打包（编译等处理）的工具webpack



##### 225. 对象深度克隆的简单实现

```js
function deepClone(obj){
var newObj= obj instanceof Array ? []:{};
for(var item in obj){
var temple= typeof obj[item] == 'object' ? deepClone(obj[item]):obj[item];
newObj[item] = temple;
}
return newObj;
}
```

##### 226. 实现一个once函数，传入函数参数只执行一次

```
function ones(func){
  var tag=true;
  return function(){
    if(tag==true){
    func.apply(null,arguments);
    tag=false;
  }
  return undefined
  }
}
```



##### 228. js监听对象属性的改变

1. 在ES5中可以通过Object.defineProperty来实现已有属性的监听
2. 在ES6中可以通过Proxy来实现

##### 229. 如何实现一个私有变量，用getName方法可以访问，不能直接访问

1. 通过defineProperty来实现

   ````js
   obj={
   	name:yuxiaoliang,
   	getName:function(){
   		return this.name
   	}
   }
   object.defineProperty(obj,"name",{
   ````

   

2. 通过函数的创建形式

   ```js
   function product(){
     var name='yuxiaoliang';
     this.getName=function(){
     	return name;
   	}
   }
   var obj=new product();
   ```

   

##### 230. ==和===、以及Object.is的区别

(1) ==

主要存在：强制转换成number,null==undefined

" "==0  //true

"0"==0  //true

" " !="0" //true

123=="123" //true

null==undefined //true

(2)Object.js

主要的区别就是+0！=-0 而NaN==NaN
(相对比===和==的改进)



##### 231. setTimeout、setInterval和requestAnimationFrame之间的区别

与setTimeout和setInterval不同，requestAnimationFrame不需要设置时间间隔，
大多数电脑显示器的刷新频率是60Hz，大概相当于每秒钟重绘60次。大多数浏览器都会对重绘操作加以限制，不超过显示器的重绘频率，因为即使超过那个频率用户体验也不会有提升。因此，最平滑动画的最佳循环间隔是1000ms/60，约等于16.6ms。

RAF采用的是系统时间间隔，不会因为前面的任务，不会影响RAF，但是如果前面的任务多的话，
会响应setTimeout和setInterval真正运行时的时间间隔。

特点：
（1）requestAnimationFrame会把每一帧中的所有DOM操作集中起来，在一次重绘或回流中就完成，并且重绘或回流的时间间隔紧紧跟随浏览器的刷新频率。

（2）在隐藏或不可见的元素中，requestAnimationFrame将不会进行重绘或回流，这当然就意味着更少的CPU、GPU和内存使用量

（3）requestAnimationFrame是由浏览器专门为动画提供的API，在运行时浏览器会自动优化方法的调用，并且如果页面不是激活状态下的话，动画会自动暂停，有效节省了CPU开销。



##### 232 实现一个两列等高布局，讲讲思路

为了实现两列等高，可以给每列加上 padding-bottom:9999px;

margin-bottom:-9999px;同时父元素设置overflow:hidden;



##### 233. 自己实现一个bind函数

原理：通过apply或者call方法来实现。

考虑到原型链: 为什么要考虑？因为在new 一个bind过生成的新函数的时候，必须的条件是要继承原函数的原型

````
Function.prototype.bind=function(obj,arg){
var arg=Array.prototype.slice.call(arguments,1);
var context=this;
var bound=function(newArg){
arg=arg.concat(Array.prototype.slice.call(newArg));
return context.apply(obj,arg);
}
var F=function(){}
````



##### 237. 如何实现sleep的效果（es5或者es6）

1. while循环的方式

   ```js
   function sleep(ms){
     var start=Date.now(),expire=start+ms;
     while(Date.now()<expire);
     console.log('1111');
     return;
   }
   ```

   

2. 通过promise来实现

   ```
   function sleep(ms){
   var temple=new Promise(
   (resolve)=>{
   console.log(111);setTimeout(resolve,ms)
   });
   return temple
   }
   sleep(500).then(function(){
   //console.log(222)
   })
   ```

3. 通过async封装

   ```
   function sleep(ms){
   return new Promise((resolve)=>setTimeout(resolve,ms));
   }
   async function test(){
   var temple=await sleep(1000);
   console.log(1111)
   return temple
   }
   test();
   ```

   

4. 通过generate来实现

   ```
   function* sleep(ms){
   yield new Promise(function(resolve,reject){
   console.log(111);
   setTimeout(resolve,ms);
   })
   }
   sleep(500).next().value.then(function(){console.log(2222)})
   ```

   

##### 238. 简单的实现一个promise

[首先明](https://promisesaplus.com/)[确什么是promiseA+规范，参考规范的地址：primise](https://promisesaplus.com/)

A+规范

如何实现一个promise，参考我的文章：

[实现一个完美符合Promise/A+规范的Promise](https://github.com/forthealllight/blog/issues/4)

一般不会问的很详细，只要能写出上述文章中的v1.0版本的简单promise即可。



##### 239. Function._proto_(getPrototypeOf)是什么？

获取一个对象的原型，在chrome中可以通过_proto_的形式，或者在ES6中可以通过Object.getPrototypeOf的形式。

那么Function.proto是什么么？也就是说Function由什么对象继承而来，我们来做如下判别。

Function.__proto__==Object.prototype //false

Function.__proto__==Function.prototype//true

我们发现Function的原型也是Function。

我们用图可以来明确这个关系：

<img width="646" alt="2018-07-10 2 38 27" src="https://user-images.githubusercontent.com/17233651/42493275-f55d0860-844e-11e8-983f-e04189a4f3d8.png">



##### 240 . 实现js中所有对象的深度克隆（包装对象，Date对象，正则对象）

通过递归可以简单实现对象的深度克隆，但是这种方法不管是ES6还是ES5实现，都有同样的缺陷，就是只能实现特定的object的深度复制（比如数组和函数），不能实现包装对象Number，String ， Boolean，以及Date对象，RegExp对象的复制。

##### 241 简单实现Node的Events模块

简介：观察者模式或者说订阅模式，它定义了对象间的一种一对多的关系，让多个观察者对象同时监听某一个主题对象，当一个对象发生改变时，所有依赖于它的对象都将得到通知。

node中的Events模块就是通过观察者模式来实现的：

```js
var events=require('events');
var eventEmitter=new events.EventEmitter();
eventEmitter.on('say',function(name){
	console.log('Hello',name);
})
eventEmitter.emit('say','Jony yu');
```

这样，eventEmitter发出say事件，通过On接收，并且输出结果，这就是一个订阅模式的实现，下面我们来简单的实现一个Events模块的EventEmitter。



实现简单的Event模块的emit和on方法

```
function Events(){
this.on=function(eventName,callBack){
if(!this.handles){
this.handles={};
}
if(!this.handles[eventName]){
this.handles[eventName]=[];
}
this.handles[eventName].push(callBack);
}
this.emit=function(eventName,obj){
if(this.handles[eventName]){
for(var i=0;o<this.handles[eventName].length;i++){
this.handles[eventName][i](obj);
}
}
}
return this;
}
```

这样我们就定义了Events，现在我们可以开始来调用：

```
var events=new Events();
events.on('say',function(name){
console.log('Hello',nama)
});
events.emit('say','Jony yu');
```

每个对象是独立的

​	因为是通过new的方式，每次生成的对象都是不相同的，因此：

```
var event1=new Events();
var event2=new Events();
event1.on('say',function(){
console.log('Jony event1');
});
event2.on('say',function(){
console.log('Jony event2');
})
event1.emit('say');
event2.emit('say');
```



##### 242. 箭头函数中this指向举例

```
var a=11;
function test2(){
this.a=22;
let b=()=>{console.log(this.a)}
b();
}
var x=new test2();
```

##### 243. js判断类型

判断方法：typeof()，instanceof，Object.prototype.toString.call()等



##### 244. 数组常用方法

push()，pop()，shift()，unshift()，splice()，sort()，reverse()，map()等



##### 245. 数组去重

法一：indexOf循环去重

法二：ES6 Set去重；Array.from(new Set(array))

法三：Object 键值对去重；把数组的值存成 Object 的 key 值，比如 Object[value1] = true，在判断另一个值的时候，如果 Object[value2]存在的话，就说明该值是重复的。

##### 246. 闭包 有什么用

（1）什么是闭包：

闭包是指有权访问另外一个函数作用域中的变量的函数。

闭包就是函数的局部变量集合，只是这些局部变量在函数返回后会继续存在。闭包就是就是函数的“堆栈”在函数返回后并不释放，我们也可以理解为这些函数堆栈并不在栈上分配而是在堆上分配。当在一个函数内定义另外一个函数就会产生闭包。

（2）为什么要用：

匿名自执行函数：我们知道所有的变量，如果不加上var关键字，则默认的会添加到全局对象的属性上去，这样的临时变量加入全局对象有很多坏处，比如：别的函数可能误用这些变量；造成全局对象过于庞大，影响访问速度(因为变量的取值是需要从原型链上遍历的)。除了每次使用变量都是用var关键字外，我们在实际情况下经常遇到这样一种情况，即有的函数只需要执行一次，其内部变量无需维护，可以用闭包。

结果缓存：我们开发中会碰到很多情况，设想我们有一个处理过程很耗时的函数对象，每次调用都会花费很长时间，那么我们就需要将计算出来的值存储起来，当调用这个函数的时候，首先在缓存中查找，如果找不到，则进行计算，然后更新缓存并返回值，如果找到了，直接返回查找到的值即可。闭包正是可以做到这一点，因为它不会释放外部的引用，从而函数内部的值可以得以保留。

封装：实现类和继承等。



##### 247. 事件代理在捕获阶段的实际应用

可以在父元素层面阻止事件向子元素传播，也可代替子元素执行某些操作。



##### 248. 去除字符串首尾空格

使用正则(^\s*)|(\s*$)即可



##### 249. 性能优化

减少HTTP请求

使用内容发布网络（CDN）

添加本地缓存

压缩资源文件

将CSS样式表放在顶部，把javascript放在底部（浏览器的运行机制决定）

避免使用CSS表达式

减少DNS查询

使用外部javascript和CSS

避免重定向

图片lazyLoad



##### 250. 来讲讲JS的闭包吧

闭包是指有权访问另外一个函数作用域中的变量的函数。

闭包就是函数的局部变量集合，只是这些局部变量在函数返回后会继续存在。闭包就是就是函数的“堆栈”在函数返回后并不释放，我们也可以理解为这些函数堆栈并不在栈上分配而是在堆上分配。当在一个函数内定义另外一个函数就会产生闭包。

（2）为什么要用：

匿名自执行函数：我们知道所有的变量，如果不加上var关键字，则默认的会添加到全局对象的属性上去，这样的临时变量加入全局对象有很多坏处，比如：别的函数可能误用这些变量；造成全局对象过于庞大，影响访问速度(因为变量的取值是需要从原型链上遍历的)。除了每次使用变量都是用var关键字外，我们在实际情况下经常遇到这样一种情况，即有的函数只需要执行一次，其内部变量无需维护，可以用闭包。

结果缓存：我们开发中会碰到很多情况，设想我们有一个处理过程很耗时的函数对象，每次调用都会花费很长时间，那么我们就需要将计算出来的值存储起来，当调用这个函数的时候，首先在缓存中查找，如果找不到，则进行计算，然后更新缓存并返回值，如果找到了，直接返回查找到的值即可。闭包正是可以做到这一点，因为它不会释放外部的引用，从而函数内部的值可以得以保留。



##### 251. 能来讲讲JS的语言特性吗

运行在客户端浏览器上；

不用预编译，直接解析执行代码；

是弱类型语言，较为灵活；

与操作系统无关，[跨平台](https://www.baidu.com/s?wd=跨平台&tn=24004469_oem_dg&rsv_dl=gh_pl_sl_csd)的语言；

脚本语言、解释性语言



##### 252. 如何判断一个数组(讲到typeof差点掉坑里)

```
Object.prototype.toString.call()
instanceof
```



##### 253. 你说到typeof，能不能加一个限制条件达到判断条件

typeof只能判断是object,可以判断一下是否拥有数组的方法



##### 254. JS实现跨域

JSONP：通过动态创建script，再请求一个带参网址实现跨域通信。document.domain + iframe跨域：两个页面都通过js强制设置document.domain为基础主域，就实现了同域。

location.hash + iframe跨域：a欲与b跨域相互通信，通过中间页c来实现。 三个页面，不同域之间利用iframe的location.hash传值，相同域之间直接js访问来通信。

window.name + iframe跨域：通过iframe的src属性由外域转向本地域，跨域数据即由iframe的window.name从外域传递到本地域。

postMessage跨域：可以跨域操作的window属性之一。

CORS：服务端设置Access-Control-Allow-Origin即可，前端无须设置，若要带cookie请求，前后端都需要设置。

代理跨域：启一个代理服务器，实现数据的转发



##### 255. Js基本数据类型

基本数据类型：undefined、null、number、boolean、string、symbol



##### 256.  js的命名方式



##### 257. js深度拷贝一个元素的具体实现

````
var deepCopy = function(obj) {
if (typeof obj !== 'object') return;
var newObj = obj instanceof Array ? [] : {};
for (var key in obj) {
if (obj.hasOwnProperty(key)) {
newObj[key] = typeof obj[key] === 'object' ? deepCopy(obj[key]) : obj[key];
}
}
return newObj;
}
````

##### 258. 之前说了ES6set可以数组去重，是否还有数组去重的方法

法一：indexOf循环去重

法二：Object 键值对去重；把数组的值存成 Object 的 key 值，比如 Object[value1] = true，在判断另一个值的时候，如果 Object[value2]存在的话，就说明该值是重复的。

##### 259. 重排和重绘，讲讲看

重绘（repaint或redraw）：当盒子的位置、大小以及其他属性，例如颜色、字体大小等都确定下来之后，浏览器便把这些原色都按照各自的特性绘制一遍，将内容呈现在页面上。重绘是指一个元素外观的改变所触发的浏览器行为，浏览器会根据元素的新属性重新绘制，使元素呈现新的外观。

触发重绘的条件：改变元素外观属性。如：color，background-color等。

注意：table及其内部元素可能需要多次计算才能确定好其在渲染树中节点的属性值，比同等元素要多花两倍时间，这就是我们尽量避免使用table布局页面的原因之一。

重排（重构/回流/reflow）：当渲染树中的一部分(或全部)因为元素的规模尺寸，布局，隐藏等改变而需要重新构建, 这就称为回流(reflow)。每个页面至少需要一次回流，就是在页面第一次加载的时候。

重绘和重排的关系：在回流的时候，浏览器会使渲染树中受到影响的部分失效，并重新构造这部分渲染树，完成回流后，浏览器会重新绘制受影响的部分到屏幕中，该过程称为重绘。所以，重排必定会引发重绘，但重绘不一定会引发重排。



##### 262. 跨域的原理

跨域，是指浏览器不能执行其他网站的脚本。它是由浏览器的同源策略造成的，是浏览器对JavaScript实施的安全限制，那么只要协议、域名、端口有任何一个不同，都被当作是不同的域。跨域原理，即是通过各种方式，避开浏览器的安全限制。



##### 264. null == undefined为什么

要比较相等性之前，不能将null 和 undefined 转换成其他任何值，但 null == undefined 会返回 true 。ECMAScript规范中是这样定义的。



##### 265. this的指向 哪几种

默认绑定：全局环境中，this默认绑定到window。

隐式绑定：一般地，被直接对象所包含的函数调用时，也称为方法调用，this隐式绑定到该直接对象。

隐式丢失：隐式丢失是指被隐式绑定的函数丢失绑定对象，从而默认绑定到window。显式绑定：通过call()、apply()、bind()方法把对象绑定到this上，叫做显式绑定。

new绑定：如果函数或者方法调用之前带有关键字new，它就构成构造函数调用。对于this绑定来说，称为new绑定。

【1】构造函数通常不使用return关键字，它们通常初始化新对象，当构造函数的函数体执行完毕时，它会显式返回。在这种情况下，构造函数调用表达式的计算结果就是这个新对象的值。

【2】如果构造函数使用return语句但没有指定返回值，或者返回一个原始值，那么这时将忽略返回值，同时使用这个新对象作为调用结果。

【3】如果构造函数显式地使用return语句返回一个对象，那么调用表达式的值就是这个对象。



##### 266. 暂停死区

在代码块内，使用let、const命令声明变量之前，该变量都是不可用的。这在语法上，称为“暂时性死区”



##### 267. AngularJS双向绑定原理

Angular将双向绑定转换为一堆watch表达式，然后递归这些表达式检查是否发生过变化，如果变了则执行相应的watcher函数（指view上的指令，如ng-bind，ng-show等或是{{}}）。等到model中的值不再发生变化，也就不会再有watcher被触发，一个完整的digest循环就完成了。

Angular中在view上声明的事件指令，如：ng-click、ng-change等，会将浏览器的事件转发给$scope上相应的model的响应函数。等待相应函数改变model，紧接着触发脏检查机制刷新view。

watch表达式：可以是一个函数、可以是$scope上的一个属性名，也可以是一个字符串形式的表达式。$watch函数所监听的对象叫做watch表达式。watcher函数：指在view上的指令（ngBind，ngShow、ngHide等）以及{{}}表达式，他们所注册的函数。每一个watcher对象都包括：监听函数，上次变化的值，获取监听表达式的方法以及监听表达式，最后还包括是否需要使用深度对比（angular.equals()）



##### 269. 简历中提到了requestAnimationFrame，请问是怎么使用的

requestAnimationFrame() 方法告诉浏览器您希望执行动画并请求浏览器在下一次重绘之前调用指定的函数来更新动画。该方法使用一个回调函数作为参数，这个回调函数会在浏览器重绘之前调用。



##### 270. 有一个游戏叫做Flappy Bird，就是一只小鸟在飞，前面是无尽的沙漠，上下不断有钢管生成，你要躲避钢管。然后小明在玩这个游戏时候老是卡顿甚至崩溃，说出原因（3-5个）以及解决办法（3-5个）

原因可能是：

1.内存溢出问题。

2.资源过大问题。

3.资源加载问题。

4.canvas绘制频率问题

解决办法：

1.针对内存溢出问题，我们应该在钢管离开可视区域后，销毁钢管，让垃圾收集器回收钢管，因为不断生成的钢管不及时清理容易导致内存溢出游戏崩溃。

2.针对资源过大问题，我们应该选择图片文件大小更小的图片格式，比如使用webp、png格式的图片，因为绘制图片需要较大计算量。

3.针对资源加载问题，我们应该在可视区域之前就预加载好资源，如果在可视区域生成钢管的话，用户的体验就认为钢管是卡顿后才生成的，不流畅。

4.针对canvas绘制频率问题，我们应该需要知道大部分显示器刷新频率为60次/s,因此游戏的每一帧绘制间隔时间需要小于1000/60=16.7ms，才能让用户觉得不卡顿。

（注意因为这是单机游戏，所以回答与网络无关）



##### 274. 什么是按需加载

当用户触发了动作时才加载对应的功能。触发的动作，是要看具体的业务场景而言，包括但不限于以下几个情况：鼠标点击、输入文字、拉动滚动条，鼠标移动、窗口大小更改等。加载的文件，可以是JS、图片、CSS、HTML等。



##### 275. 说一下什么是virtual dom

用JavaScript 对象结构表示 DOM 树的结构；然后用这个树构建一个真正的 DOM 树，插到文档当中 当状态变更的时候，重新构造一棵新的对象树。然后用新的树和旧的树进行比较，记录两棵树差异 把所记录的差异应用到所构建的真正的DOM树上，视图就更新了。Virtual DOM 本质上就是在 JS 和 DOM 之间做了一个缓存。



##### 277. ant-design优点和缺点

优点：组件非常全面，样式效果也都比较不错。

缺点：框架自定义程度低，默认UI风格修改困难。



##### 278. JS中继承实现的几种方式，

1、原型链继承，将父类的实例作为子类的原型，他的特点是实例是子类的实例也是父类的实例，父类新增的原型方法/属性，子类都能够访问，并且原型链继承简单易于实现，缺点是来自原型对象的所有属性被所有实例共享，无法实现多继承，无法向父类构造函数传参。

2、构造继承，使用父类的构造函数来增强子类实例，即复制父类的实例属性给子类，

构造继承可以向父类传递参数，可以实现多继承，通过call多个父类对象。但是构造继承只能继承父类的实例属性和方法，不能继承原型属性和方法，无法实现函数服用，每个子类都有父类实例函数的副本，影响性能

3、实例继承，为父类实例添加新特性，作为子类实例返回，实例继承的特点是不限制调用方法，不管是new 子类（）还是子类（）返回的对象具有相同的效果，缺点是实例是父类的实例，不是子类的实例，不支持多继承

4、拷贝继承：特点：支持多继承，缺点：效率较低，内存占用高（因为要拷贝父类的属性）无法获取父类不可枚举的方法（不可枚举方法，不能使用for in 访问到）

5、组合继承：通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用

6、寄生组合继承：通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性，避免的组合继承的缺点



##### 279. 写一个函数，第一秒打印1，第二秒打印2

```
for(let i=0;i<5;i++){
setTimeout(function(){
console.log(i)
},1000*i)
}

for(var i=0;i<5;i++){
(function(i){
setTimeout(function(){
console.log(i)
},1000*i)
})(i)
}
```

##### 280. vue的生命周期

Vue实例有一个完整的生命周期，也就是从开始创建、初始化数据、编译模板、挂载Dom、渲染→更新→渲染、销毁等一系列过程，我们称这是Vue的生命周期。通俗说就是Vue实例从创建到销毁的过程，就是生命周期。

每一个组件或者实例都会经历一个完整的生命周期，总共分为三个阶段：初始化、运行中、销毁。

实例、组件通过new Vue() 创建出来之后会初始化事件和生命周期，然后就会执行beforeCreate钩子函数，这个时候，数据还没有挂载呢，只是一个空壳，无法访问到数据和真实的dom，一般不做操作

挂载数据，绑定事件等等，然后执行created函数，这个时候已经可以使用到数据，也可以更改数据,在这里更改数据不会触发updated函数，在这里可以在渲染前倒数第二次更改数据的机会，不会触发其他的钩子函数，一般可以在这里做初始数据的获取

接下来开始找实例或者组件对应的模板，编译模板为虚拟dom放入到render函数中准备渲染，然后执行beforeMount钩子函数，在这个函数中虚拟dom已经创建完成，马上就要渲染,在这里也可以更改数据，不会触发updated，在这里可以在渲染前最后一次更改数据的机会，不会触发其他的钩子函数，一般可以在这里做初始数据的获取

接下来开始render，渲染出真实dom，然后执行mounted钩子函数，此时，组件已经出现在页面中，数据、真实dom都已经处理好了,事件都已经挂载好了，可以在这里操作真实dom等事情...

当组件或实例的数据更改之后，会立即执行beforeUpdate，然后vue的虚拟dom机制会重新构建虚拟dom与上一次的虚拟dom树利用diff算法进行对比之后重新渲染，一般不做什么事儿

当更新完成后，执行updated，数据已经更改完成，dom也重新render完成，可以操作更新后的虚拟dom

当经过某种途径调用$destroy方法后，立即执行beforeDestroy，一般在这里做一些善后工作，例如清除计时器、清除非指令绑定的事件等等

组件的数据绑定、监听...去掉后只剩下dom空壳，这个时候，执行destroyed，在这里做善后工作也可以



##### 281. 简单介绍一下symbol

Symbol是ES6 的新增属性，代表用给定名称作为唯一标识，这种类型的值可以这样创建，let id=symbol(“id”)

Symbl确保唯一，即使采用相同的名称，也会产生不同的值，我们创建一个字段，仅为知道对应symbol的人能访问，使用symbol很有用，symbol并不是100%隐藏，有内置方法Object.getOwnPropertySymbols(obj)可以获得所有的symbol。
也有一个方法Reflect.ownKeys(obj)返回对象所有的键，包括symbol。

所以并不是真正隐藏。但大多数库内置方法和语法结构遵循通用约定他们是隐藏的，



##### 282. 什么是事件监听

addEventListener()方法，用于向指定元素添加事件句柄，它可以更简单的控制事件，语法为

element.addEventListener(event, function, useCapture);

第一个参数是事件的类型(如 "click" 或 "mousedown").

第二个参数是事件触发后调用的函数。

第三个参数是个布尔值用于描述事件是冒泡还是捕获。该参数是可选的。

事件传递有两种方式，冒泡和捕获

事件传递定义了元素事件触发的顺序，如果你将P元素插入到div元素中，用户点击P元素，

在冒泡中，内部元素先被触发，然后再触发外部元素，

捕获中，外部元素先被触发，在触发内部元素，



##### 283. 介绍一下promise，及其底层如何实现

Promise是一个对象，保存着未来将要结束的事件，她有两个特征:

1、对象的状态不受外部影响，Promise对象代表一个异步操作，有三种状态，pending进行中，fulfilled已成功，rejected已失败，只有异步操作的结果，才可以决定当前是哪一种状态，任何其他操作都无法改变这个状态，这也就是promise名字的由来

2、一旦状态改变，就不会再变，promise对象状态改变只有两种可能，从pending改到fulfilled或者从pending改到rejected，只要这两种情况发生，状态就凝固了，不会再改变，这个时候就称为定型resolved,

Promise的基本用法，

````
let promise1 = new Promise(function(resolve,reject){
setTimeout(function(){
resolve('ok')
},1000)
})
promise1.then(function success(val){
console.log(val)
})
````



##### 286. js原型链，原型链的顶端是什么？Object的原型是什么？Object的原型的原型是什么？在数组原型链上实现删除数组重复数据的方法

能够把这个讲清楚弄明白是一件很困难的事，

首先明白原型是什么，在ES6之前，JS没有类和继承的概念，JS是通过原型来实现继承的，在JS中一个构造函数默认带有一个prototype属性，这个的属性值是一个对象，同时这个prototype对象自带有一个constructor属性，这个属性指向这个构造函数，同时每一个实例都会有一个_proto_属性指向这个prototype对象，我们可以把这个叫做隐式原型，我们在使用一个实例的方法的时候，会先检查这个实例中是否有这个方法，没有的话就会检查这个prototype对象是否有这个方法，

基于这个规则，如果让原型对象指向另一个类型的实例，即constructor1.protoytpe=instance2，这时候如果试图引用constructor1构造的实例instance1的某个属性p1,

首先会在instance1内部属性中找一遍，

接着会在instance1._proto_（constructor1.prototype）即是instance2中寻找p1

搜寻轨迹：instance1->instance2->constructor2.prototype……->Object.prototype;这即是原型链，原型链顶端是Object.prototype

补充学习：

每个函数都有一个prototype属性，这个属性指向了一个对象，这个对象正是调用该函数而创建的实例的原型，那么什么是原型呢，可以这样理解，每一个JavaScript对象在创建的时候就会预制管理另一个对象，这个对象就是我们所说的原型，每一个对象都会从原型继承属性

https://www.nowcoder.com/ta/review-frontend/review?page=286



##### 287. 什么是js的闭包？有什么作用，用闭包写个单例模式

MDN对闭包的定义是：闭包是指那些能够访问自由变量的函数，自由变量是指在函数中使用的，但既不是函数参数又不是函数的局部变量的变量，由此可以看出，闭包=函数+函数能够访问的自由变量，所以从技术的角度讲，所有JS函数都是闭包，但是这是理论上的闭包，还有一个实践角度上的闭包，从实践角度上来说，只有满足1、即使创建它的上下文已经销毁，它仍然存在，2、在代码中引入了自由变量，才称为闭包

闭包的应用：

模仿块级作用域。2、保存外部函数的变量。3、封装私有变量



##### 288. promise+Generator+Async的使用

https://www.nowcoder.com/ta/review-frontend/review?page=288

Promise

解决的问题:回调地狱

Promise规范:

promise有三种状态，等待（pending）、已完成（fulfilled/resolved）、已拒绝（rejected）.Promise的状态只能从“等待”转到“完成”或者“拒绝”，不能逆向转换，同时“完成”和“拒绝”也不能相互转换.

promise 必须提供一个 then方法以访问其当前值、终值和据因。promise.then(resolve, reject),resolve 和 reject都是可选参数。如果 resolve 或reject 不是函数，其必须被忽略.

then 方法必须返回一个 promise 对象.

使用:

实例化promise对象需要传入函数(包含两个参数),resolve和reject,内部确定状态.resolve和reject函数可以传入参数在回调函数中使用.
resolve和reject都是函数,传入的参数在then的回调函数中接收.





##### 289. 事件委托以及冒泡原理。

事件委托是利用冒泡阶段的运行机制来实现的，就是把一个元素响应事件的函数委托到另一个元素，一般是把一组元素的事件委托到他的父元素上，委托的优点是

减少内存消耗，节约效率

动态绑定事件

事件冒泡，就是元素自身的事件被触发后，如果父元素有相同的事件，如onclick事件，那么元素本身的触发状态就会传递，也就是冒到父元素，父元素的相同事件也会一级一级根据嵌套关系向外触发，直到document/window，冒泡过程结束。



##### 290. 写个函数，可以转化下划线命名到驼峰命名



##### 292. JS中string的startwith和indexof两种方法的区别

JS中startwith函数，其参数有3个，stringObj,要搜索的字符串对象，str，搜索的字符串，position，可选，从哪个位置开始搜索，如果以position开始的字符串以搜索字符串开头，则返回true，否则返回false

Indexof函数，indexof函数可返回某个指定字符串在字符串中首次出现的位置，



##### 293. js字符串转数字的方法

通过函数parseInt（），可解析一个字符串，并返回一个整数，语法为parseInt（string ,radix）

string：被解析的字符串

radix：表示要解析的数字的基数，默认是十进制，如果radix<2或>36,则返回NaN



##### 294. let const var的区别 ，什么是块级作用域，如何用ES5的方法实现块级作用域（立即执行函数），ES6 呢

提起这三个最明显的区别是var声明的变量是全局或者整个函数块的，而let,const声明的变量是块级的变量，var声明的变量存在变量提升，let,const不存在，let声明的变量允许重新赋值，const不允许，



##### 295. ES6箭头函数的特性

ES6 增加了箭头函数，基本语法为

let func = value => value;

相当于

let func = function (value) {

return value;

};

箭头函数与普通函数的区别在于：

1、箭头函数没有this，所以需要通过查找作用域链来确定this的值，这就意味着如果箭头函数被非箭头函数包含，this绑定的就是最近一层非箭头函数的this，

2、箭头函数没有自己的arguments对象，但是可以访问外围函数的arguments对象

3、不能通过new关键字调用，同样也没有new.target值和原型



##### 296. setTimeout和Promise的执行顺序

settimeout这种异步操作的回调，只有主线程中没有执行任何同步代码的前提下，才会执行异步回调，而settimeout（fun,0）表示立刻执行，也就是用来改变任务的执行顺序，要求浏览器尽可能快的进行回调

promise何时执行，由上图可知promise新建后立即执行，所以promise构造函数里代码同步执行的，

then方法指向的回调将在当前脚本所有同步任务执行完成后执行，

那么then为什么比settimeout执行的早呢，因为settimeout（fun,0）不是真的立即执行，

经过测试得出结论：执行顺序为：同步执行的代码-》promise.then->settimeout



##### 297 有了解过事件模型吗，DOM0级和DOM2级有什么区别，DOM的分级是什么

JSDOM事件流存在如下三个阶段：

事件捕获阶段

处于目标阶段

事件冒泡阶段

JSDOM标准事件流的触发的先后顺序为：先捕获再冒泡，点击DOM节点时，事件传播顺序：事件捕获阶段，从上往下传播，然后到达事件目标节点，最后是冒泡阶段，从下往上传播

DOM节点添加事件监听方法addEventListener，中参数capture可以指定该监听是添加在事件捕获阶段还是事件冒泡阶段，为false是事件冒泡，为true是事件捕获，并非所有的事件都支持冒泡，比如focus，blur等等，我们可以通过event.bubbles来判断

事件模型有三个常用方法：

event.stopPropagation:阻止捕获和冒泡阶段中，当前事件的进一步传播，

event.stopImmediatePropagetion，阻止调用相同事件的其他侦听器，

event.preventDefault，取消该事件（假如事件是可取消的）而不停止事件的进一步传播，

event.target：指向触发事件的元素，在事件冒泡过程中这个值不变

event.currentTarget = this，时间帮顶的当前元素，只有被点击时目标元素的target才会等于currentTarget，

最后，对于执行顺序的问题，如果DOM节点同时绑定了两个事件监听函数，一个用于捕获，一个用于冒泡，那么两个事件的执行顺序真的是先捕获在冒泡吗，答案是否定的，绑定在被点击元素的事件是按照代码添加顺序执行的，其他函数是先捕获再冒泡



##### 297. 有了解过事件模型吗，DOM0级和DOM2级有什么区别，DOM的分级是什么

JSDOM事件流存在如下三个阶段：

事件捕获阶段

处于目标阶段

事件冒泡阶段

JSDOM标准事件流的触发的先后顺序为：先捕获再冒泡，点击DOM节点时，事件传播顺序：事件捕获阶段，从上往下传播，然后到达事件目标节点，最后是冒泡阶段，从下往上传播

DOM节点添加事件监听方法addEventListener，中参数capture可以指定该监听是添加在事件捕获阶段还是事件冒泡阶段，为false是事件冒泡，为true是事件捕获，并非所有的事件都支持冒泡，比如focus，blur等等，我们可以通过event.bubbles来判断

事件模型有三个常用方法：

event.stopPropagation:阻止捕获和冒泡阶段中，当前事件的进一步传播，

event.stopImmediatePropagetion，阻止调用相同事件的其他侦听器，

event.preventDefault，取消该事件（假如事件是可取消的）而不停止事件的进一步传播，

event.target：指向触发事件的元素，在事件冒泡过程中这个值不变

event.currentTarget = this，时间帮顶的当前元素，只有被点击时目标元素的target才会等于currentTarget，

最后，对于执行顺序的问题，如果DOM节点同时绑定了两个事件监听函数，一个用于捕获，一个用于冒泡，那么两个事件的执行顺序真的是先捕获在冒泡吗，答案是否定的，绑定在被点击元素的事件是按照代码添加顺序执行的，其他函数是先捕获再冒泡

##### 299. JS的基本数据类型有哪些，基本数据类型和引用数据类型的区别，NaN是什么的缩写，JS的作用域类型，undefined==null返回的结果是什么，undefined与null的区别在哪，写一个函数判断变量类型

JS的基本数据类型有字符串，数字，布尔，对象，Null，Undefined,基本数据类型是按值访问的，也就是说我们可以操作保存在变量中的实际的值，

基本数据类型和引用数据类型的区别如下：

基本数据类型的值是不可变的，任何方法都无法改变一个基本类型的值，当这个变量重新赋值后看起来变量的值是改变了，但是这里变量名只是指向变量的一个指针，所以改变的是指针的指向改变，该变量是不变的，但是引用类型可以改变

基本数据类型不可以添加属性和方法，但是引用类型可以

基本数据类型的赋值是简单赋值，如果从一个变量向另一个变量赋值基本类型的值，会在变量对象上创建一个新值，然后把该值复制到为新变量分配的位置上，引用数据类型的赋值是对象引用，

基本数据类型的比较是值的比较，引用类型的比较是引用的比较，比较对象的内存地址是否相同

基本数据类型是存放在栈区的，引用数据类型同事保存在栈区和堆区

NaN是JS中的特殊值，表示非数字，NaN不是数字，但是他的数据类型是数字，它不等于任何值，包括自身，在布尔运算时被当做false，NaN与任何数运算得到的结果都是NaN，党员算失败或者运算无法返回正确的数值的就会返回NaN，一些数学函数的运算结果也会出现NaN ,

JS的作用域类型：

一般认为的作用域是词法作用域，此外JS还提供了一些动态改变作用域的方法，常见的作用域类型有：

函数作用域，如果在函数内部我们给未定义的一个变量赋值，这个变量会转变成为一个全局变量，

块作用域：块作用域吧标识符限制在{}中，

改变函数作用域的方法：

eval（），这个方法接受一个字符串作为参数，并将其中的内容视为好像在书写时就存在于程序中这个位置的代码，

with关键字：通常被当做重复引用同一个对象的多个属性的快捷方式



undefined与null：目前null和undefined基本是同义的，只有一些细微的差别，null表示没有对象，undefined表示缺少值，就是此处应该有一个值但是还没有定义

undefined == null；//返回值是true

undefined === null; //返回值是false



此外了解== 和===的区别：

在做==比较时。不同类型的数据会先转换成一致后在做比较，===中如果类型不一致就直接返回false，一致的才会比较

类型判断函数，使用typeof即可，首先判断是否为null，之后用typeof哦按段，如果是object的话，再用array.isarray判断是否为数组，如果是数字的话用isNaN判断是否是NaN即可
扩展学习：

JS采用的是词法作用域，也就是静态作用域，所以函数的作用域在函数定义的时候就决定了，



##### 300. setTimeout(fn,100);100毫秒是如何权衡的

setTimeout()函数只是将事件插入了任务列表，必须等到当前代码执行完，主线程才会去执行它指定的回调函数，有可能要等很久，所以没有办法保证回调函数一定会在setTimeout指定的时间内执行，100毫秒是插入队列的时间+等待的时间



##### 301. JS的垃圾回收机制





##### 303. 怎么获得对象上的属性：比如说通过Object.key（）

从ES5开始，有三种方法可以列出对象的属性

for（let I in obj）该方法依次访问一个对象及其原型链中所有可枚举的类型

object.keys:返回一个数组，包括所有可枚举的属性名称

object.getOwnPropertyNames:返回一个数组包含不可枚举的属性



##### 304. 简单讲一讲ES6的一些新特性

ES6在变量的声明和定义方面增加了let、const声明变量，有局部变量的概念，赋值中有比较吸引人的结构赋值，同时ES6对字符串、 数组、正则、对象、函数等拓展了一些方法，如字符串方面的模板字符串、函数方面的默认参数、对象方面属性的简洁表达方式，ES6也 引入了新的数据类型symbol，新的数据结构set和map,symbol可以通过typeof检测出来，为解决异步回调问题，引入了promise和 generator，还有最为吸引人了实现Class和模块，通过Class可以更好的面向对象编程，使用模块加载方便模块化编程，当然考虑到 浏览器兼容性，我们在实际开发中需要使用babel进行编译

重要的特性：

块级作用域：ES5只有全局作用域和函数作用域，块级作用域的好处是不再需要立即执行的函数表达式，循环体中的闭包不再有问题

rest参数：用于获取函数的多余参数，这样就不需要使用arguments对象了，

promise:一种异步编程的解决方案，比传统的解决方案回调函数和事件更合理强大

模块化：其模块功能主要有两个命令构成，export和import，export命令用于规定模块的对外接口，import命令用于输入其他模块提供的功能



##### 305. call和apply是用来做什么？

Call和apply的作用是一模一样的，只是传参的形式有区别而已

1、改变this的指向

2、借用别的对象的方法，

3、调用函数，因为apply，call方法会使函数立即执行



##### 306. 了解事件代理吗，这样做有什么好处

事件代理/事件委托：利用了事件冒泡，只指定一个事件处理程序，就可以管理某一类型的事件，

简而言之：事件代理就是说我们将事件添加到本来要添加的事件的父节点，将事件委托给父节点来触发处理函数，这通常会使用在大量的同级元素需要添加同一类事件的时候，比如一个动态的非常多的列表，需要为每个列表项都添加点击事件，这时就可以使用事件代理，通过判断e.target.nodeName来判断发生的具体元素，这样做的好处是减少事件绑定，同事动态的DOM结构任然可以监听，事件代理发生在冒泡阶段



##### 307. 如何使不同页面之间进行通信



##### 308. 如何写一个继承？

原型链继承

核心： 将父类的实例作为子类的原型

特点：

非常纯粹的继承关系，实例是子类的实例，也是父类的实例

父类新增原型方法/原型属性，子类都能访问到

简单，易于实现

缺点：

要想为子类新增属性和方法，不能放到构造器中

无法实现多继承

来自原型对象的所有属性被所有实例共享

创建子类实例时，无法向父类构造函数传参



构造继承

核心：使用父类的构造函数来增强子类实例，等于是复制父类的实例属性给子类（没用到原型）

特点：

解决了子类实例共享父类引用属性的问题

创建子类实例时，可以向父类传递参数

可以实现多继承（call多个父类对象）

缺点：

实例并不是父类的实例，只是子类的实例

只能继承父类的实例属性和方法，不能继承原型属性/方法

无法实现函数复用，每个子类都有父类实例函数的副本，影响性能



实例继承

核心：为父类实例添加新特性，作为子类实例返回

特点：

不限制调用方式，不管是new 子类()还是子类(),返回的对象具有相同的效果

缺点：

实例是父类的实例，不是子类的实例

不支持多继承



拷贝继承

特点：

支持多继承

缺点：

效率较低，内存占用高（因为要拷贝父类的属性）



组合继承

核心：通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用

特点：

可以继承实例属性/方法，也可以继承原型属性/方法

既是子类的实例，也是父类的实例

不存在引用属性共享问题

可传参

函数可复用



寄生组合继承

核心：通过调用父类构造，继承父类的属性并保留传参的优点，然后通过将父类实例作为子类原型，实现函数复用



##### 320. js加载过程阻塞，解决方法。

指定script标签的async属性。

如果async="async"，脚本相对于页面的其余部分异步地执行（当页面继续进行解析时，脚本将被执行）

如果不使用async 且 defer="defer"：脚本将在页面完成解析时执行



##### 322. JavaScript中的轮播实现原理？假如一个页面上有两个轮播，你会怎么实现？

图片轮播的原理就是图片排成一行，然后准备一个只有一张图片大小的容器，对这个容器设置超出部分隐藏，在控制定时器来让这些图片整体左移或右移，这样呈现出来的效果就是图片在轮播了。

如果有两个轮播，可封装一个轮播组件，供两处调用

##### 328. class

ES6提供了更接近传统语言的写法，引入了Class（类）这个概念，作为对象的模板。通过class关键字，可以定义类。



##### 329. 口述数组去重

法一：indexOf循环去重

法二：ES6 Set去重；Array.from(new Set(array))

法三：Object 键值对去重；把数组的值存成 Object 的 key 值，比如 Object[value1] = true，在判断另一个值的时候，如果 Object[value2]存在的话，就说明该值是重复的。



##### 333 箭头函数和function有什么区别

箭头函数根本就没有绑定自己的this，在箭头函数中调用 this 时，仅仅是简单的沿着作用域链向上寻找，找到最近的一个 this 拿来使用



##### 334. new操作符原理

\1. 创建一个类的实例：创建一个空对象obj，然后把这个空对象的__proto__设置为构造函数的prototype。

\2. 初始化实例：构造函数被传入参数并调用，关键字this被设定指向该实例obj。

\3. 返回实例obj。



##### 335. bind,apply,call

apply：调用一个对象的一个方法，用另一个对象替换当前对象。例如：B.apply(A, arguments);即A对象应用B对象的方法。

call：调用一个对象的一个方法，用另一个对象替换当前对象。例如：B.call(A, args1,args2);即A对象调用B对象的方法。

bind除了返回是函数以外，它的参数和call一样。



##### 342. 事件委托

把一个元素响应事件（click、keydown......）的函数委托到另一个元素；

优点：减少内存消耗、动态绑定事件。





##### 349. 事件代理

事件代理是利用事件的冒泡原理来实现的，何为事件冒泡呢？就是事件从最深的节点开始，然后逐步向上传播事件，举个例子：页面上有这么一个节点树，div>ul>li>a;比如给最里面的a加一个click点击事件，那么这个事件就会一层一层的往外执行，执行顺序a>li>ul>div，有这样一个机制，那么我们给最外面的div加点击事件，那么里面的ul，li，a做点击事件的时候，都会冒泡到最外层的div上，所以都会触发，这就是事件代理，代理它们父级代为执行事件。



##### 350. Eventloop

任务队列中，在每一次事件循环中，macrotask只会提取一个执行，而microtask会一直提取，直到microsoft队列为空为止。

也就是说如果某个microtask任务被推入到执行中，那么当主线程任务执行完成后，会循环调用该队列任务中的下一个任务来执行，直到该任务队列到最后一个任务为止。而事件循环每次只会入栈一个macrotask,主线程执行完成该任务后又会检查microtasks队列并完成里面的所有任务后再执行macrotask的任务。

macrotasks: setTimeout, setInterval, setImmediate, I/O, UI rendering
microtasks: process.nextTick, Promise, MutationObserver



##### 356. 如何实现跨域

JSONP：通过动态创建script，再请求一个带参网址实现跨域通信。document.domain + iframe跨域：两个页面都通过js强制设置document.domain为基础主域，就实现了同域。

location.hash + iframe跨域：a欲与b跨域相互通信，通过中间页c来实现。 三个页面，不同域之间利用iframe的location.hash传值，相同域之间直接js访问来通信。

window.name + iframe跨域：通过iframe的src属性由外域转向本地域，跨域数据即由iframe的window.name从外域传递到本地域。

postMessage跨域：可以跨域操作的window属性之一。

CORS：服务端设置Access-Control-Allow-Origin即可，前端无须设置，若要带cookie请求，前后端都需要设置。

代理跨域：起一个代理服务器，实现数据的转发



##### 375. webpack和gulp区别（模块化与流的区别）

gulp强调的是前端开发的工作流程，我们可以通过配置一系列的task，定义task处理的事务（例如文件压缩合并、雪碧图、启动server、版本控制等），然后定义执行顺序，来让gulp执行这些task，从而构建项目的整个前端开发流程。

webpack是一个前端模块化方案，更侧重模块打包，我们可以把开发中的所有资源（图片、js文件、css文件等）都看成模块，通过loader（加载器）和plugins（插件）对资源进行处理，打包成符合生产环境部署的前端资源。



##### 376. redux用处

在组件化的应用中，会有着大量的组件层级关系，深嵌套的组件与浅层父组件进行数据交互，变得十分繁琐困难。而redux，站在一个服务级别的角度，可以毫无阻碍地将应用的状态传递到每一个层级的组件中。redux就相当于整个应用的管家。



redux里常用方法

提供 [getState()](https://www.nowcoder.com/ta/review-frontend/review?page=377#getState) 方法获取 state；

提供 [dispatch(action)](https://www.nowcoder.com/ta/review-frontend/review?page=377#dispatch) 方法更新 state；

通过 [subscribe(listener)](https://www.nowcoder.com/ta/review-frontend/review?page=377#subscribe) 注册监听器;

等等



##### 386. 介绍一下react

React 是一个用于构建用户界面的 JAVASCRIPT 库。React主要用于构建UI，很多人认为 React 是 MVC 中的 V（视图）

React特点有：

1.声明式设计 −React采用声明范式，可以轻松描述应用。

2.高效 −React通过对DOM的模拟，最大限度地减少与DOM的交互。

3.灵活 −React可以与已知的库或框架很好地配合。

4.JSX − JSX 是 JavaScript 语法的扩展。React 开发不一定使用 JSX ，但我们建议使用它。

5.组件 − 通过 React 构建组件，使得代码更加容易得到复用，能够很好的应用在大项目的开发中。

6.单向响应的数据流 − React 实现了单向响应的数据流，从而减少了重复代码，这也是它为什么比传统数据绑定更简单。



##### 387. React单项数据流

在React中，数据是单向流动的，是从上向下的方向，即从父组件到子组件的方向。

state和props是其中重要的概念，如果顶层组件初始化props，那么React会向下遍历整颗组件树，重新渲染相关的子组件。其中state表示的是每个组件中内部的的状态，这些状态只在组件内部改变。
把组件看成是一个函数，那么他接受props作为参数，内部由state作为函数的内部参数，返回一个虚拟dom的实现。



##### 388. react生命周期函数和react组件的生命周期

React的组件在第一次挂在的时候首先获取父组件传递的props，接着获取初始的state值，接着经历挂载阶段的三个生命周期函数，也就是ComponentWillMount，render，ComponentDidMount，这三个函数分别代表组件将会挂载，组件渲染，组件挂载完毕三个阶段，在组件挂载完成后，组件的props和state的任意改变都会导致组建进入更新状态，在组件更新阶段，如果是props改变，则进入ComponentWillReceiveProps函数，接着进入ComponentShouldUpdate进行判断是否需要更新，如果是state改变则直接进入ComponentShouldUpdate判定，这个默认是true，当判定不需要更新的话，组件继续运行，需要更新的话则依次进入ComponentWillMount，render，ComponentDidMount三个函数，当组件卸载时，会首先进入生命周期函数ComponentWillUnmount,之后才进行卸载，如图

![reactLifeCycle](/Users/linghankong/Desktop/MAIN_LinghanKong_Repos/LeetCode-Havermeyer/doc/Assets/reactLifeCycle.png)



React的生命周期函数：

初始化阶段：getDefaultProps获取实例的默认属性，getInitialState获取每个实例的初始化状态，ComponentWillMount：组件将被装载，渲染到页面上，render：组件在这里生成虚拟的DOM节点，ComponentDidMount:组件真正被装载之后

运行中状态： componentWillReceiveProps:组件将要接收到属性的时候调用 shouldComponentUpdate:组件接受到新属性或者新状态的时候（可以返回 false，接收数据后不更新，阻止 render 调用，后面的函数不会被继续执行了）shouldComponentUpdate 这个方法用来判断是否需要调用 render 方法重新描绘 dom。因为 dom 的描绘非常消耗性能，如果我们能在 shouldComponentUpdate 方法中能够写出更优化的 dom diff 算法，可以极大的提高性能。 componentWillUpdate:组件即将更新不能修改属性和状态 render:组件重新描绘 componentDidUpdate:组件已经更新 销毁阶段： componentWillUnmount:组件即将销毁



##### 390. reactJs的组件交流

React组件之间的交流方式可以分为以下三种

1. 父组件向子组件传值:主要是利用props来进行交流

2. 子组件向父组件传值：子组件通过控制自己的state然后告诉父组件的点击状态。然后在父组件中展示出来

3. 没有任何嵌套关系的组件之间传值：如果组件之间没有任何关系，组件嵌套层次比较深（个人认为 2 层以上已经算深了），或者你为了一些组件能够订阅、写入一些信号，不想让组件之间插入一个组件，让两个组件处于独立的关系。对于事件系统，这里有 2 个基本操作步骤：订阅（subscribe）/监听（listen）一个事件通知，并发送（send）/触发（trigger）/发布（publish）/发送（dispatch）一个事件通知那些想要的组件。



##### 391. 有了解过react的虚拟DOM吗，虚拟DOM是怎么对比的呢

当然是使用的diff算法，diff算法有三种优化形式：

tree diff：将新旧两颗DOM树按照层级遍历，只对同级的DOM节点进行比较，即同一父节点下的所有子节点，当发现节点已经不存在，则该节点及其子节点会被完全删除，不会进一步比较

component diff：不同组件之间的对比，如果组件类型相同，暂不更新，否则删除旧的组件，再创建一个新的组件，插入到删除组件的位置

element diff:在类型相同的组件内，再继续对比组件内部的元素，



##### 394. 怎么获取真正的dom

ReactDOM.findDOMNode()或this.refs



##### 397. setState之后的流程

在代码中调用setState函数之后，React 会将传入的参数对象与组件当前的状态合并，然后触发所谓的调和过程（Reconciliation）。 经过调和过程，React 会以相对高效的方式根据新的状态构建 React 元素树并且着手重新渲染整个UI界面。 在 React 得到元素树之后，React 会自动计算出新的树与老树的节点差异，然后根据差异对界面进行最小化重渲染。 在差异计算算法中，React 能够相对精确地知道哪些位置发生了改变以及应该如何改变，这就保证了按需更新，而不是全部重新渲染。



##### 398. react高阶组件知道吗？

高阶组件接收React组件作为参数，并且返回一个新的React组件。高阶组件本质上也是一个函数，并不是一个组件。



##### 406. TCP建立连接的三次握手过程

第一次握手：起初两端都处于CLOSED关闭状态，Client将标志位SYN置为1，随机产生一个值seq=x，并将该数据包发送给Server，Client进入SYN-SENT状态，等待Server确认；

第二次握手：Server收到数据包后由标志位SYN=1得知Client请求建立连接，Server将标志位SYN和ACK都置为1，ack=x+1，随机产生一个值seq=y，并将该数据包发送给Client以确认连接请求，Server进入SYN-RCVD状态，此时操作系统为该TCP连接分配TCP缓存和变量；

第三次握手：Client收到确认后，检查ack是否为x+1，ACK是否为1，如果正确则将标志位ACK置为1，ack=y+1，并且此时操作系统为该TCP连接分配TCP缓存和变量，并将该数据包发送给Server，Server检查ack是否为y+1，ACK是否为1，如果正确则连接建立成功，Client和Server进入ESTABLISHED状态，完成三次握手，随后Client和Server就可以开始传输数据。



##### 407. cdn原理

CDN的全称是Content Delivery Network，即内容分发网络。CDN的基本原理是广泛采用各种缓存服务器，将这些缓存服务器分布到用户访问相对集中的地区或网络中，在用户访问网站时，利用全局负载技术将用户的访问指向距离最近的工作正常的缓存服务器上，由缓存服务器直接响

##### 413. OSI七层模型

osi七层模型可以说是面试必考基础了

从上到下分别是：

应用层：文件传输，常用协议HTTP，snmp,FTP ,

表示层：数据格式化，代码转换，数据加密，

会话层：建立，解除会话

传输层：提供端对端的接口，tcp,udp

网络层：为数据包选择路由，IP，icmp

数据链路层：传输有地址的帧

物理层：二进制的数据形式在物理媒体上传输数据



##### 417. TCP/IP的网络模型

TCP/IP模型是一系列网络协议的总称，这些协议的目的是使得计算机之间可以进行信息交换，

TCP/IP模型四层架构从下到上分别是链路层，网络层，传输层，应用层

链路层的作用是负责建立电路连接，是整个网络的物理基础，典型的协议包括以太网，ADSL等，

网络层负责分配地址和传送二进制数据，主要协议是IP协议，

传输层负责传送文本数据，主要协议是TCP

应用层负责传送各种最终形态的数据，是直接与用户信息打交道的层，主要协议是http，ftp等





##### 421. 什么是进程 线程

进程，是并发执行的程序在执行过程中分配和管理资源的基本单位，是一个动态概念，竞争计算机系统资源的基本单位。

线程，是进程的一部分，一个没有线程的进程可以被看作是单线程的。线程有时又被称为轻权进程或轻量级进程，也是 CPU 调度的一个基本单位。

##### 422. 线程的那些资源共享，那些资源不共享

共享的资源有

a. 堆  由于堆是在进程空间中开辟出来的，所以它是理所当然地被共享的；因此new出来的都是共享的（16位平台上分全局堆和局部堆，局部堆是独享的）

b. 全局变量 它是与具体某一函数无关的，所以也与特定线程无关；因此也是共享的

c. 静态变量虽然对于局部变量来说，它在代码中是“放”在某一函数中的，但是其存放位置和全局变量一样，存于堆中开辟的.bss和.data段，是共享的

d. 文件等公用资源  这个是共享的，使用这些公共资源的线程必须同步。Win32 提供了几种同步资源的方式，包括信号、临界区、事件和互斥体。

独享的资源有

a. 栈 栈是独享的

b. 寄存器  这个可能会误解，因为电脑的寄存器是物理的，每个线程去取值难道不一样吗？其实线程里存放的是副本，包括程序计数器PC

##### 427. 进程间的通信方式有哪些

总共有八种，面试中只要能大概答上三四种方式的原理就可以了

1、无名管道：半双工的通信方式，数据只能单向流动且只能在具有亲缘关系的进程间使用

2、高级管道：将另一个程序当作一个新的进程在当前程序进程中启动，则这个进程算是当前程序的子进程，

3、有名管道，：也是半双工的通信方式，但是允许没有亲缘进程之间的通信

4、消息队列：消息队列是有消息的链表，存放在内核中，并由消息队列标识符标识，消息队列克服了信号传递信息少，管道只能承载无格式字节流以及缓冲区大小受限的缺点

5、信号量：信号量是一个计数器，可以用来控制多个进程对共享资源的访问，它常作为一种锁机制，防止某进程正在访问共享资源时，其他进程也访问该资源，

6、信号：用于通知接受进程某个事件已经发生

7、共享内存：共享内存就是映射一段能被其他进程所访问的内存。这段共享内存由一个进程创建，但是多个进程可以访问，共享内存是最快的IPC 方式，往往与其他通信机制配合使用

8、套接字：可用于不同机器之间的进程通信



##### 428. Redis和 mysql

（1）类型上

从类型上来说，mysql是关系型数据库，redis是缓存数据库

（2）作用上

mysql用于持久化的存储数据到硬盘，功能强大，但是速度较慢

redis用于存储使用较为频繁的数据到缓存中，读取速度快

（3）需求上

mysql和redis因为需求的不同，一般都是配合使用。



##### 431 尾递归

如果一个函数中所有递归形式的调用都出现在函数的末尾，我们称这个递归函数是尾递归的。当递归调用是整个函数体中最后执行的语句且它的返回值不属于表达式的一部分时，这个递归调用就是尾递归

##### 444. 设计模式：单例，工厂，发布订阅

单例模式：在它的核心结构中值包含一个被称为单例的特殊类。一个类只有一个实例，即一个类只有一个对象实例。

工厂模式：在创建对象时不会对客户端暴露创建逻辑，并且是通过使用一个共同的接口来指向新创建的对象。

发布订阅模式：在[软件架构](https://baike.baidu.com/item/软件架构)中，发布订阅是一种[消息](https://baike.baidu.com/item/消息)[范式](https://baike.baidu.com/item/范式)，消息的发送者（称为发布者）不会将消息直接发送给特定的接收者（称为订阅者）。而是将发布的消息分为不同的类别，无需了解哪些订阅者（如果有的话）可能存在。同样的，订阅者可以表达对一个或多个类别的兴趣，只接收感兴趣的消息，无需了解哪些发布者（如果有的话）存在。

JS中常用的设计模式中，我最常用的是装饰者模式，在不改变元对象的基础上，对这个对象进行包装和拓展（包括添加属性和方法），从而使这个对象可以有更复杂的功能。





##### 从promise、process.nextTick、setTimeout出发，谈谈Event Loop中的Job queue

event loop读取任务的先后顺序，取决于任务队列（Job queue）中对于不同任务读取规则的限定

**Job queue中的执行顺序**

在Job queue中的队列分为两种类型：macro-task和microTask。我们举例来看执行顺序的规定，我们设

macro-task队列包含任务: ***a1, a2 , a3***
micro-task队列包含任务: ***b1, b2 , b3***

执行顺序为，首先执行marco-task队列开头的任务，也就是 ***a1*** 任务，执行完毕后，在执行micro-task队列里的所有任务，也就是依次执行***b1, b2 , b3***，执行完后清空micro-task中的任务，接着执行marco-task中的第二个任务，依次循环。

了解完了macro-task和micro-task两种队列的执行顺序之后，我们接着来看，真实场景下这两种类型的队列里真正包含的任务（我们以node V8引擎为例），在node V8中，这两种类型的真实任务顺序如下所示：

macro-task队列真实包含任务：

***\*script(主程序代码),setTimeout, setInterval, setImmediate, I/O, UI rendering\****

micro-task队列真实包含任务：
***process.nextTick, Promises, Object.observe, MutationObserver***

由此我们得到的执行顺序应该为：

***script(主程序代码)—>process.nextTick—>Promises...——>setTimeout——>setInterval——>setImmediate——> I/O——>UI rendering***

在ES6中macro-task队列又称为ScriptJobs，而micro-task又称PromiseJobs

同是微任务的情况下，process优先级更高



##### 响应式布局的常用解决方案对比(媒体查询、百分比、rem和vw/vh）

前端开发中，静态网页通常需要适应不同分辨率的设备，常用的自适应解决方案包括媒体查询、百分比、rem和vw/vh等。本文从px单位出发，分析了px在移动端布局中的不足，接着介绍了几种不同的自适应解决方案。

1. px和视口
2. 媒体查询
3. 百分比
4. 自适应场景下的rem解决方案
5. 通过vw/vh来实现自适应

**px和视口**

在静态网页中，我们经常用像素（px）作为单位，来描述一个元素的宽高以及定位信息。在pc端，通常认为css中,1px所表示的真实长度是固定的。

***那么，px真的是一个设备无关，跟长度单位米和分米一样是固定大小的吗？***

- 像素

  像素是网页布局的基础，一个像素表示了计算机屏幕所能显示的最小区域，像素分为两种类型：css像素和物理像素。

  我们在js或者css代码中使用的px单位就是指的是css像素，物理像素也称设备像素，只与设备或者说硬件有关，同样尺寸的屏幕，设备的密度越高，物理像素也就越多。下表表示css像素和物理像素的具体区别：

  | css像素  | 为web开发者提供，在css中使用的一个抽象单位           |
  | -------- | ---------------------------------------------------- |
  | 物理像素 | 只与设备的硬件密度有关，任何设备的物理像素都是固定的 |

  那么css像素与物理像素的转换关系是怎么样的呢？为了明确css像素和物理像素的转换关系，必须先了解视口是什么。



- 视口

  广义的视口，是指浏览器显示内容的屏幕区域，狭义的视口包括了布局视口、视觉视口和理想视口

  - 布局视图

    布局视口定义了pc网页在移动端的默认布局行为，因为通常pc的分辨率较大，布局视口默认为980px。也就是说在不设置网页的viewport的情况下，pc端的网页默认会以布局视口为基准，在移动端进行展示。因此我们可以明显看出来，默认为布局视口时，根植于pc端的网页在移动端展示很模糊。

  - 视觉视图

    视觉视口表示浏览器内看到的网站的显示区域，用户可以通过缩放来查看网页的显示内容，从而改变视觉视口。视觉视口的定义，就像拿着一个放大镜分别从不同距离观察同一个物体，视觉视口仅仅类似于放大镜中显示的内容，因此视觉视口不会影响布局视口的宽度和高度。

  - 理想视图

    理想视口或者应该全称为“理想的布局视口”，在移动设备中就是指设备的分辨率。换句话说，理想视口或者说分辨率就是给定设备物理像素的情况下，最佳的“布局视口”。

    **上述视口中，最重要的是要明确理想视口的概念，在移动端中，理想视口或者说分辨率跟物理像素之间有什么关系呢？**

    为了理清分辨率和物理像素之间的联系，我们介绍一个用DPR（Device pixel ratio）设备像素比来表示，则可以写成：

    `1 DPR = 物理像素／分辨率`

    在不缩放的情况下，一个css像素就对应一个dpr，也就是说，在不缩放

    `1 CSS像素 = 物理像素／分辨率`

    此外，在移动端的布局中，我们可以通过viewport元标签来控制布局，比如一般情况下，我们可以通过下述标签使得移动端在理想视口下布局：

    `<meta id="viewport" name="viewport" content="width=device-width; initial-scale=1.0; maximum-scale=1; user-scalable=no;">`



上述meta标签的每一个属性的详细介绍如下：

| 属性名        | 取值    | 描述                                     |
| ------------- | ------- | ---------------------------------------- |
| width         | 正整数  | 定义布局视口的宽度，单位为像素           |
| height        | 正整数  | 定义布局视口的高度，单位为像素，很少使用 |
| initial-scale | [0,10]  | 初始缩放比例，1表示不缩放                |
| minimum-scale | [0,10]  | 最小缩放比例                             |
| maximum-scale | [0,10]  | 最大缩放比例                             |
| user-scalable | yes／no | 是否允许手动缩放页面，默认值为yes        |

其中我们来看width属性，在移动端布局时，在meta标签中我们会将width设置称为device-width，device-width一般是表示分辨率的宽，通过width=device-width的设置我们就将布局视口设置成了理想的视口。

**px 与自适应**

上述我们了解到了当通过viewport元标签，设置布局视口为理想视口时，1个css像素可以表示成：

`1 CSS像素 = 物理像素／分辨率`

我们直到，在pc端的布局视口通常情况下为980px，移动端以iphone6为例，分辨率为375 * 667，也就是说布局视口在理想的情况下为375px。比如现在我们有一个750px * 1134px的视觉稿，

那么在pc端，一个css像素可以如下计算：

`PC端： 1 CSS像素 = 物理像素／分辨率 = 750 ／ 980 =0.76 px`

而在iphone6下：

`iphone6：1 CSS像素 = 物理像素 ／分辨率 = 750 ／ 375 = 2 px`

也就是说在PC端，一个CSS像素可以用0.76个物理像素来表示，而iphone6中 一个CSS像素表示了2个物理像素。此外不同的移动设备分辨率不同，也就是1个CSS像素可以表示的物理像素是不同的，因此如果在css中仅仅通过px作为长度和宽度的单位，造成的结果就是无法通过一套样式，实现各端的自适应。

***媒体查询***

在前面我们说到，不同端的设备下，在css文件中，1px所表示的物理像素的大小是不同的，因此通过一套样式，是无法实现各端的自适应。由此我们联想：

**如果一套样式不行，那么能否给每一种设备各一套不同的样式来实现自适应的效果？**

使用[@media](https://github.com/media)媒体查询可以针对不同的媒体类型定义不同的样式，特别是响应式页面，可以针对不同屏幕的大小，编写多套样式，从而达到自适应的效果。举例来说：

```css
@media screen and (max-width: 960px){
    body{
      background-color:#FF6699
    }
}

@media screen and (max-width: 768px){
    body{
      background-color:#00FF66;
    }
}

@media screen and (max-width: 550px){
    body{
      background-color:#6633FF;
    }
}

@media screen and (max-width: 320px){
    body{
      background-color:#FFFF00;
    }
}
```

上述的代码通过媒体查询定义了几套样式，通过max-width设置样式生效时的最大分辨率，上述的代码分别对分辨率在0～320px，320px～550px，550px～768px以及768px～960px的屏幕设置了不同的背景颜色。

通过媒体查询，可以通过给不同分辨率的设备编写不同的样式来实现响应式的布局，比如我们为不同分辨率的屏幕，设置不同的背景图片。比如给小屏幕手机设置[@2x](https://github.com/2x)图，为大屏幕手机设置[@3x](https://github.com/3x)图，通过媒体查询就能很方便的实现。

但是媒体查询的缺点也很明显，如果在浏览器大小改变时，需要改变的样式太多，那么多套样式代码会很繁琐。

***百分比***

除了用px结合媒体查询实现响应式布局外，我们也可以通过百分比单位 " % " 来实现响应式的效果。

比如当浏览器的宽度或者高度发生变化时，通过百分比单位，通过百分比单位可以使得浏览器中的组件的宽和高随着浏览器的变化而变化，从而实现响应式的效果。

**css中的子元素中的百分比（%）到底是谁的百分比？**

直观的理解，我们可能会认为子元素的百分比完全相对于直接父元素，height百分比相对于height，width百分比相对于width。当然这种理解是正确的，

但是根据css的盒式模型，除了height、width属性外，还具有padding、border、margin等等属性。那么这些属性设置成百分比，是根据父元素的那些属性呢？此外还有border-radius和translate等属性中的百分比，又是相对于什么呢？下面来具体分析。

1. 子元素height和width的百分比

   子元素的height或width中使用百分比，是相对于子元素的直接父元素，width相对于父元素的width，height相对于父元素的height。

2. top和bottom 、left和right

   子元素的top和bottom如果设置百分比，则相对于直接非static定位(默认定位)的父元素的高度，同样子元素的left和right如果设置百分比，则相对于直接非static定位(默认定位的)父元素的宽度。

3. padding

   子元素的padding如果设置百分比，不论是垂直方向或者是水平方向，都相对于直接父亲元素的width，而与父元素的height无关。

4. margin

   跟padding一样，margin也是如此，子元素的margin如果设置成百分比，不论是垂直方向还是水平方向，都相对于直接父元素的width。这里就不具体举例。

5. border-radius

   border-radius不一样，如果设置border-radius为百分比，则是相对于自身的宽度，除了border-radius外，还有比如translate、background-size等都是相对于自身的，这里就不一一举例。

**百分比单位布局应用**

比如我们要实现一个固定长宽比的长方形，比如要实现一个长宽比为4:3的长方形,我们可以根据padding属性来实现，因为padding不管是垂直方向还是水平方向，百分比单位都相对于父元素的宽度，因此我们可以设置padding-top为百分比来实现，长宽自适应的长方形.

**百分比单位缺点**

从上述对于百分比单位的介绍我们很容易看出如果全部使用百分比单位来实现响应式的布局，有明显的以下两个缺点：

（1）计算困难，如果我们要定义一个元素的宽度和高度，按照设计稿，必须换算成百分比单位。
（2）从小节1可以看出，各个属性中如果使用百分比，相对父元素的属性并不是唯一的。比如width和height相对于父元素的width和height，而margin、padding不管垂直还是水平方向都相对比父元素的宽度、border-radius则是相对于元素自身等等，造成我们使用百分比单位容易使布局问题变得复杂



**自适应场景下的rem解决方案**

**rem单位**

首先来看，什么是rem单位。rem是一个灵活的、可扩展的单位，由浏览器转化像素并显示。与em单位不同，rem单位无论嵌套层级如何，都只相对于浏览器的根元素（HTML元素）的font-size。默认情况下，html元素的font-size为16px，所以：

` 1 rem = 16px`

为了计算方便，通常可以将html的font-size设置成：

`html{ font-size: 62.5% }`

which is

`    1 rem = 10px`

**通过rem来实现响应式布局**

rem单位都是相对于根元素html的font-size来决定大小的,根元素的font-size相当于提供了一个基准，当页面的size发生变化时，只需要改变font-size的值，那么以rem为固定单位的元素的大小也会发生响应的变化。

因此，如果通过rem来实现响应式的布局，只需要根据视图容器的大小，动态的改变font-size即可。

```js
function refreshRem() {
    var docEl = doc.documentElement;
    var width = docEl.getBoundingClientRect().width;
    var rem = width / 10;
    docEl.style.fontSize = rem + 'px';
    flexible.rem = win.rem = rem;
}
win.addEventListener('resize', refreshRem);
```

上述代码中将视图容器分为10份，font-size用十分之一的宽度来表示，最后在header标签中执行这段代码，就可以动态定义font-size的大小，从而1rem在不同的视觉容器中表示不同的大小，用rem固定单位可以实现不同容器内布局的自适应。

**rem2px和px2rem**

如果在响应式布局中使用rem单位，那么存在一个单位换算的问题，rem2px表示从rem换算成px，这个就不说了，只要rem乘以相应的font-size中的大小，就能换算成px。更多的应用是px2rem，表示的是从px转化为rem。

比如给定的视觉稿为750px（物理像素），如果我们要将所有的布局单位都用rem来表示，一种比较笨的办法就是对所有的height和width等元素，乘以相应的比例，现将视觉稿换算成rem单位，然后一个个的用rem来表示。另一种比较方便的解决方法就是，在css中我们还是用px来表示元素的大小，最后编写完css代码之后，将css文件中的所有px单位，转化成rem单位。

px2rem的原理也很简单，重点在于预处理以px为单位的css文件，处理后将所有的px变成rem单位。可以通过两种方式来实现：

1. webpack loader的形式：

   `npm install px2rem-loader`

   在webpack的配置文件中：

   ```js
   module.exports = {
     // ...
     module: {
       rules: [{
         test: /\.css$/,
         use: [{
           loader: 'style-loader'
         }, {
           loader: 'css-loader'
         }, {
           loader: 'px2rem-loader',
           // options here
           options: {
             remUni: 75,
             remPrecision: 8
           }
         }]
       }]
     }
   }
   ```

   webpack中使用postcss plugin

   `npm install postcss-loader`

   ```js
   var px2rem = require('postcss-px2rem');
   
   module.exports = {
     module: {
       loaders: [
         {
           test: /\.css$/,
           loader: "style-loader!css-loader!postcss-loader"
         }
       ]
     },
     postcss: function() {
       return [px2rem({remUnit: 75})];
     }
   }
   ```

   

   通过rem单位，可以实现响应式的布局，特别是引入相应的postcss相关插件，免去了设计稿中的px到rem的计算。rem单位在国外的一些网站也有使用，这里所说的rem来实现布局的缺点，或者说是小缺陷是：

   

   **在响应式布局中，必须通过js来动态控制根元素font-size的大小。**

   也就是说css样式和js代码有一定的耦合性。且必须将改变font-size的代码放在css样式之前。



**通过vw/vh来实现自适应**

1. 什么是vw/vh ?

   css3中引入了一个新的单位vw/vh，与视图窗口有关，vw表示相对于视图窗口的宽度，vh表示相对于视图窗口高度，除了vw和vh外，还有vmin和vmax两个相关的单位。各个单位具体的含义如下：

   | 单位 | 含义                              |
   | ---- | --------------------------------- |
   | vw   | 相对于视窗的宽度，视窗宽度是100vw |
   | vh   | 相对于视窗的高度，视窗高度是100vh |
   | vmin | vw和vh中的较小值                  |
   | vmax | vw和vh中的较大值                  |

   这里我们发现视窗宽高都是100vw／100vh，那么vw或者vh，下简称vw，很类似百分比单位。vw和%的区别为：

   | 单位  | 含义                                                         |
   | ----- | ------------------------------------------------------------ |
   | %     | 大部分相对于祖先元素，也有相对于自身的情况比如（border-radius、translate等) |
   | vw/vh | 相对于视窗的尺寸                                             |

   从对比中我们可以发现，vw单位与百分比类似，确有区别，前面我们介绍了百分比单位的换算困难，这里的vw更像"理想的百分比单位"。任意层级元素，在使用vw单位的情况下，1vw都等于视图宽度的百分之一。

   

2. vw单位换算

   同样的，如果要将px换算成vw单位，很简单，只要确定视图的窗口大小（布局视口），如果我们将布局视口设置成分辨率大小，比如对于iphone6/7 375*667的分辨率，那么px可以通过如下方式换算成vw：

   `1px = （1/375）*100 vw`

   也可以通过postcss的相应插件，预处理css做一个自动的转换，[postcss-px-to-viewport](https://github.com/evrone/postcss-px-to-viewport)可以自动将px转化成vw。postcss-px-to-viewport的默认参数为：

   ```js
   var defaults = {
     viewportWidth: 320,
     viewportHeight: 568, 
     unitPrecision: 5,
     viewportUnit: 'vw',
     selectorBlackList: [],
     minPixelValue: 1,
     mediaQuery: false
   };
   ```

   通过指定视窗的宽度和高度，以及换算精度，就能将px转化成vw。

3. vw/vh单位的兼容性

   可以在https://caniuse.com/ 查看各个版本的浏览器对vw单位的支持性。

   从上图我们发现，绝大多数的浏览器支持vw单位，但是ie9-11不支持vmin和vmax，考虑到vmin和vmax单位不常用，vw单位在绝大部分高版本浏览器内的支持性很好，但是opera浏览器整体不支持vw单位，如果需要兼容opera浏览器的布局，不推荐使用vw。



##### [高性能滚动 scroll 及页面渲染优化 ](https://www.cnblogs.com/coco1s/p/5499469.html)

滚动优化的由来

​	滚动优化其实也不仅仅指滚动（scroll 事件），还包括了例如 resize 这类会频繁触发的事件。简单的看看：

```js
var i = 0;
window.addEventListener('scroll',function(){
    console.log(i++);
},false);
```

在绑定 scroll 、resize 这类事件时，当它发生时，它被触发的频次非常高，间隔很近。如果事件中涉及到大量的位置计算、DOM 操作、元素重绘等工作且这些工作无法在下一个 scroll 事件触发前完成，就会造成浏览器掉帧。加之用户鼠标滚动往往是连续的，就会持续触发 scroll 事件导致掉帧扩大、浏览器 CPU 使用率增加、用户体验受到影响。

在滚动事件中绑定回调应用场景也非常多，在图片的懒加载、下滑自动加载数据、侧边浮动导航栏等中有着广泛的应用。

当用户浏览网页时，拥有平滑滚动经常是被忽视但却是用户体验中至关重要的部分。当滚动表现正常时，用户就会感觉应用十分流畅，令人愉悦，反之，笨重不自然卡顿的滚动，则会给用户带来极大不舒爽的感觉。

**滚动与页面渲染的关系**

一个 Web 页面的展示，简单来说可以认为经历了以下下几个步骤：

![pageshow](../Assets/pageshow.jpeg)

- **JavaScript**：一般来说，我们会使用 JavaScript 来实现一些视觉变化的效果。比如做一个动画或者往页面里添加一些 DOM 元素等。
- **Style：**计算样式，这个过程是根据 CSS 选择器，对每个 DOM 元素匹配对应的 CSS 样式。这一步结束之后，就确定了每个 DOM 元素上该应用什么 CSS 样式规则。
- **Layout：**布局，上一步确定了每个 DOM 元素的样式规则，这一步就是具体计算每个 DOM 元素最终在屏幕上显示的大小和位置。web 页面中元素的布局是相对的，因此一个元素的布局发生变化，会联动地引发其他元素的布局发生变化。比如，`<body>` 元素的宽度的变化会影响其子元素的宽度，其子元素宽度的变化也会继续对其孙子元素产生影响。因此对于浏览器来说，布局过程是经常发生的。
- **Paint：**绘制，本质上就是填充像素的过程。包括绘制文字、颜色、图像、边框和阴影等，也就是一个 DOM 元素所有的可视效果。一般来说，这个绘制过程是在多个层上完成的。
- **Composite：**渲染层合并，由上一步可知，对页面中 DOM 元素的绘制是在多个层上进行的。在每个层上完成绘制过程之后，浏览器会将所有层按照合理的顺序合并成一个图层，然后显示在屏幕上。对于有位置重叠的元素的页面，这个过程尤其重要，因为一旦图层的合并顺序出错，将会导致元素显示异常。

简单来说，网页生成的时候，至少会渲染（Layout+Paint）一次。用户访问的过程中，还会不断重新的重排（reflow）和重绘（repaint）。

其中，用户 scroll 和 resize 行为（即是滑动页面和改变窗口大小）会导致页面不断的重新渲染。

当你滚动页面时，浏览器可能会需要绘制这些层(有时也被称为合成层)里的一些像素。通过元素分组，当某个层的内容改变时，我们只需要更新该层的结构，并仅仅重绘和栅格化渲染层结构里变化的那一部分，而无需完全重绘。显然，如果当你滚动时，像视差网站([戳我看看](http://waaac.co/))这样有东西在移动时，有可能在多层导致大面积的内容调整，这会导致大量的绘制工作。

**防抖（Debouncing）和节流（Throttling）**

scroll 事件本身会触发页面的重新渲染，同时 scroll 事件的 handler 又会被高频度的触发, 因此事件的 handler 内部不应该有复杂操作，例如 DOM 操作就不应该放在事件处理中.

针对此类高频度触发事件问题（例如页面 scroll ，屏幕 resize，监听用户输入等），下面介绍两种常用的解决方法，防抖和节流。

**防抖（Debouncing）**

防抖技术即是可以把多个顺序地调用合并成一次，也就是在一定时间内，规定事件被触发的次数.

```js
// 简单的防抖动函数
function debounce(func, wait, immediate) {
    // 定时器变量
    var timeout;
    return function() {
        // 每次触发 scroll handler 时先清除定时器
        clearTimeout(timeout);
        // 指定 xx ms 后触发真正想进行的操作 handler
        timeout = setTimeout(func, wait);
    };
};
 
// 实际想绑定在 scroll 事件上的 handler
function realFunc(){
    console.log("Success");
}
 
// 采用了防抖动
window.addEventListener('scroll',debounce(realFunc,500));
// 没采用防抖动
window.addEventListener('scroll',realFunc);
```

上面简单的防抖的例子可以拿到浏览器下试一下，大概功能就是如果 500ms 内没有连续触发两次 scroll 事件，那么才会触发我们真正想在 scroll 事件中触发的函数。

上面的示例可以更好的封装一下：

```js
// 防抖动函数
function debounce(func, wait, immediate) {
    var timeout;
    return function() {
        var context = this, args = arguments;
        var later = function() {
            timeout = null;
            if (!immediate) func.apply(context, args);
        };
        var callNow = immediate && !timeout;
        clearTimeout(timeout);
        timeout = setTimeout(later, wait);
        if (callNow) func.apply(context, args);
    };
};
 
var myEfficientFn = debounce(function() {
    // 滚动中的真正的操作
}, 250);
 
// 绑定监听
window.addEventListener('resize', myEfficientFn);
```

**节流（Throttling）**

防抖函数确实不错，但是也存在问题，譬如图片的懒加载，我希望在下滑过程中图片不断的被加载出来，而不是只有当我停止下滑时候，图片才被加载出来。又或者下滑时候的数据的 ajax 请求加载也是同理。

这个时候，我们希望即使页面在不断被滚动，但是滚动 handler 也可以以一定的频率被触发（譬如 250ms 触发一次），这类场景，就要用到另一种技巧，称为节流函数（throttling）。



节流函数，只允许一个函数在 X 毫秒内执行一次。

与防抖相比，节流函数最主要的不同在于它保证在 X 毫秒内至少执行一次我们希望触发的事件 handler。

与防抖相比，节流函数多了一个 mustRun 属性，代表 mustRun 毫秒内，必然会触发一次 handler ，同样是利用定时器，看看简单的示例：



```js
// 简单的节流函数
function throttle(func, wait, mustRun) {
    var timeout,
        startTime = new Date();
 
    return function() {
        var context = this,
            args = arguments,
            curTime = new Date();
 
        clearTimeout(timeout);
        // 如果达到了规定的触发时间间隔，触发 handler
        if(curTime - startTime >= mustRun){
            func.apply(context,args);
            startTime = curTime;
        // 没达到触发间隔，重新设定定时器
        }else{
            timeout = setTimeout(func, wait);
        }
    };
};
// 实际想绑定在 scroll 事件上的 handler
function realFunc(){
    console.log("Success");
}
// 采用了节流函数
window.addEventListener('scroll',throttle(realFunc,500,1000));
```

上面简单的节流函数的例子可以拿到浏览器下试一下，大概功能就是如果在一段时间内 scroll 触发的间隔一直短于 500ms ，那么能保证事件我们希望调用的 handler 至少在 1000ms 内会触发一次。

**使用 rAF（requestAnimationFrame）触发滚动事件**

上面介绍的抖动与节流实现的方式都是借助了定时器 setTimeout ，但是如果页面只需要兼容高版本浏览器或应用在移动端，又或者页面需要追求高精度的效果，那么可以使用浏览器的原生方法 rAF（requestAnimationFrame）。

**requestAnimationFrame**

window.requestAnimationFrame() 这个方法是用来在页面重绘之前，通知浏览器调用一个指定的函数。这个方法接受一个函数为参，该函数会在重绘前调用。

rAF 常用于 web 动画的制作，用于准确控制页面的帧刷新渲染，让动画效果更加流畅，当然它的作用不仅仅局限于动画制作，我们可以利用它的特性将它视为一个定时器。（当然它不是定时器）

通常来说，rAF 被调用的频率是每秒 60 次，也就是 1000/60 ，触发频率大概是 16.7ms 。（当执行复杂操作时，当它发现无法维持 60fps 的频率时，它会把频率降低到 30fps 来保持帧数的稳定。）

简单而言，使用 requestAnimationFrame 来触发滚动事件 === `throttle(func, xx, 1000/60) ``//xx 代表 xx ms内不会重复触发事件 handler`

```js
var ticking = false; // rAF 触发锁
 
function onScroll(){
  if(!ticking) {
    requestAnimationFrame(realFunc);
    ticking = true;
  }
}
 
function realFunc(){
    // do something...
    console.log("Success");
    ticking = false;
}
// 滚动事件监听
window.addEventListener('scroll', onScroll, false);
```



使用 requestAnimationFrame 优缺点并存，首先我们不得不考虑它的兼容问题，其次因为它只能实现以 16.7ms 的频率来触发，代表它的可调节性十分差。但是相比 throttle(func, xx, 16.7) ，用于更复杂的场景时，rAF 可能效果更佳，性能更好。

- 防抖动：防抖技术即是可以把多个顺序地调用合并成一次，也就是在一定时间内，规定事件被触发的次数。
- 节流函数：只允许一个函数在 X 毫秒内执行一次，只有当上一次函数执行后过了你规定的时间间隔，才能进行下一次该函数的调用。
- rAF：16.7ms 触发一次 handler，降低了可控性，但是提升了性能和精确度



**简化 scroll 内的操作**

上面介绍的方法都是如何去优化 scroll 事件的触发，避免 scroll 事件过度消耗资源的。

但是从本质上而言，我们应该尽量去精简 scroll 事件的 handler ，将一些变量的初始化、不依赖于滚动位置变化的计算等都应当在 scroll 事件外提前就绪。

建议如下：

**避免在**scroll 事件**中修改样式属性 **将样式操作从 scroll 事件中剥离\**

输入事件处理函数，比如 scroll / touch 事件的处理，都会在 requestAnimationFrame 之前被调用执行。

因此，如果你在 scroll 事件的处理函数中做了修改样式属性的操作，那么这些操作会被浏览器暂存起来。然后在调用 requestAnimationFrame 的时候，如果你在一开始做了读取样式属性的操作，那么这将会导致触发浏览器的强制同步布局。

输入事件处理函数，比如 scroll / touch 事件的处理，都会在 requestAnimationFrame 之前被调用执行。

因此，如果你在 scroll 事件的处理函数中做了修改样式属性的操作，那么这些操作会被浏览器暂存起来。然后在调用 requestAnimationFrame 的时候，如果你在一开始做了读取样式属性的操作，那么这将会导致触发浏览器的强制同步布局。

**滑动过程中尝试使用 pointer-events: none 禁止鼠标事件**



大部分人可能都不认识这个属性，嗯，那么它是干什么用的呢？

[pointer-events](https://developer.mozilla.org/zh-CN/docs/Web/CSS/pointer-events) 是一个 CSS 属性，可以有多个不同的值，属性的一部分值仅仅与 SVG 有关联，这里我们只关注 pointer-events: none 的情况，大概的意思就是禁止鼠标行为，应用了该属性后，譬如鼠标点击，hover 等功能都将失效，即是元素不会成为鼠标事件的 target。

可以就近 F12 打开开发者工具面板，给 <body> 标签添加上 pointer-events: none 样式，然后在页面上感受下效果，发现所有鼠标事件都被禁止了。

pointer-events: none 可用来提高滚动时的帧频。的确，当滚动时，鼠标悬停在某些元素上，则触发其上的 hover 效果，然而这些影响通常不被用户注意，并多半导致滚动出现问题。对 body 元素应用 pointer-events: none ，禁用了包括 hover 在内的鼠标事件，从而提高滚动性能。



##### [javascript中this的指向问题](https://www.cnblogs.com/chengxs/p/8679313.html)

**1：this永远指向一个对象；**

**2：this的指向完全取决于函数调用的位置；**

使用 JavaScript 开发的时候，很多开发者多多少少会被 `this` 的指向搞蒙圈，但是实际上，关于 `this` 的指向，记住最核心的一句话： 

**哪个对象调用函数，函数里面的this指向哪个对象。** 分为两种情况：浏览器 和 Nodejs

**一、普通函数调用**

这个情况没特殊意外，就是指向全局对象-window。

- 使用let

  ```js
  /*普通函数调用*/
  let username = "uName";
  function fn(){
      console.log(this.username);   //undefined
  }
  fn();
  
  // nodejs : undefined
  // browser : undefined
  ```

  

- 使用var

  ```js
  var name = "uName";
  function fn(){
      console.log(this.name);
  }
  fn();
  
  // nodejs: undefined
  // browser: uName
  ```

- 使用window

- let和var区别：

  **`（1）let` 允许把变量的作用域限制在块级域中；var** **申明变量要么是全局的，要么是函数级的，而无法是块级的**

  



**二、对象函数调用**

 这个相信不难理解，就是**哪个函数调用，this指向哪里**。

```js
/*对象函数调用*/
//window.name='程新松';
//var name='程新松';
let name='程新松';
let obj={
    id:201102304,
    fn:function(){
        console.log(this.name);  //undefined
        console.log(this.id);   //201102304
    }
}
obj.fn();
```

很明显，第一次就是输出 `obj.name` ，但是没有这个name属性，输出的结果undefined。而第二次输出`obj.id，有这个id属性，`输出 201102304，**因为 `this` 指向 `obj` 。**

```js
/*需要注意的情况*/
let obj1={
    a:111
}
let obj2={
    a:222,
    fn:function(){
        console.log(this.a);
    }
}
obj1.fn=obj2.fn;
obj1.fn();  //111
```

这个也不难理解，虽然 `obj1.fn` 是从 `obj2.fn` 赋值而来，但是调用函数的是 `obj1` ，所以 **`this` 指向 `obj1`** 。





**三、构造函数调用**

```js
/*构造函数调用*/
let structureClass=function(){
    this.name='程新松';
}
let subClass1=new structureClass();
console.log(subClass1.name); // 程新松

let subClass=new structureClass();
subClass.name='成才';
console.log(subClass.name); //成
```

**在构造函数里面返回一个对象，会直接返回这个对象，而不是执行构造函数后创建的对象**

```js
let structureClass=function(){
    this.name='程新松';
    return {
        username:'saucxs'
    }
}
let subClass1=new structureClass();
console.log(subClass1); // {username:'saucxs'}
console.log(subClass1.name); // undefined
```







**四、apply和call调用**

1. **apply和call简单来说就是会改变传入函数的this。**

   ```js
   /*apply和call调用*/
   let obj1={
       name:'程新松'
   };
   let obj2={
       name:'saucxs',
       fn:function(){
           console.log(this.name);
       }
   }
   obj2.fn.call(obj1); // 程新松
   ```

   **此时虽然是 `obj2` 调用方法，但是使用 了 `call` ，动态的把 `this` 指向到 `obj1` 。相当于这个 `obj2.fn` 这个执行环境是 `obj1` 。**

   **`call` 和 `apply` 两个主要用途：**

   1.改变 `this` 的指向（把 `this` 从 `obj2` 指向到 `obj1` ）

   2.方法借用（ `obj1` 没有 `fn` ，只是借用 `obj2` 方法）

2. **call与apply区别**

    `call` 和 `apply` 的作用，完全一样，唯一的区别就是在参数上面。

   **`call` 接收的参数不固定，第一个参数是函数体内 `this` 的指向，第二个参数以下是依次传入的参数。**

   **apply接收两个参数，第一个参数也是函数体内 `this` 的指向。第二个参数是一个集合对象（数组或者类数组）**

   ```js
   /*apply和call区别*/
   let fn=function(a,b,c){
       console.log(a,b,c);
   }
   let arrArray=[1,2,3];
   fn.call(window,arrArray); // [1, 2, 3], undefined, undefined
   fn.apply(window,arrArray); // 1 2 3
   ```

   

**五、箭头函数调用**

 首先不得不说，ES6 提供了箭头函数，增加了我们的开发效率，**但是在箭头函数里面，没有 `this`** ，**箭头函数里面的 `this` 是继承外面的环境**。

```js
/*箭头函数调用*/
let obj={
    name:'程新松',
    fn:function(){
        setTimeout(function(){console.log(this.name)})
    }
}
obj.fn(); // undefined
```

不难发现，虽然 **fn()** 里面的 **this** 是指向 **obj** ，但是，传给 **setTimeout** 的是普通函数， **this** 指向是 **window** ， **window** 下面没有 **name** ，所以这里输出 **underfind** 。

```js
//换成箭头函数
let obj={
    name:"程新松",
    fn:function(){
        setTimeout(()=>{console.log(this.name)});
    }
}
obj.fn(); // 程新松

```

这次输出 **程新松** 是因为，传给 **setTimeout** 的是箭头函数，然后箭头函数里面没有 **this** ，所以要向上层作用域查找，在这个例子上， **setTimeout** 的上层作用域是 **fn** 。而 **fn** 里面的 **this** 指向 **obj** ，所以 **setTimeout** 里面的箭头函数的 **this** ，指向 **obj** 。所以输出 **程新松**。



##### 什么是BFC？什么条件下会触发？应用场景有哪些

> 浮动元素和绝对定位元素，非块级盒子的块级容器（例如 inline-blocks, table-cells, 和 table-captions），以及overflow值不为"visiable"的块级盒子，都会为他们的内容创建新的BFC（Block Fromatting Context， 即块级格式上下文）。

一个HTML元素要创建BFC，则满足下列的任意一个或多个条件即可： 下列方式会创建块格式化上下文：

1. 根元素
2. 浮动元素（元素的 float 不是 none）
3. 绝对定位元素（元素的 position 为 absolute 或 fixed）
4. 行内块元素（元素的 display 为 inline-block）
5. 表格单元格（元素的 display为 table-cell，HTML表格单元格默认为该值）
6. 表格标题（元素的 display 为 table-caption，HTML表格标题默认为该值）
7. 匿名表格单元格元素（元素的 display为 table、table-row、 table-row-group、table-header-group、table-footer-group（分别是HTML table、row、tbody、thead、tfoot的默认属性）或 inline-table）
8. overflow 值不为 visible 的块元素 -弹性元素（display为 flex 或 inline-flex元素的直接子元素） 网格元素（display为 grid 或 inline-grid 元素的直接子元素） 等等。

**BFC渲染规则**

- BFC是一个独立的容器，外面的元素不会影响里面的元素
- 计算BFC高度的时候浮动元素也会参与计算
- BFC的区域不会与浮动元素的box重叠
- Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠**

**应用场景**

不适用BFC情况下，子元素使用浮动，父元素高度会塌陷

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .inner {
            height: 50px;
            width: 50px;
            background: green;
            float: left;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="inner"></div>
    </div>
</body>
</html>
```

将父级元素设为BFC后

```css
.container {
    overflow: hidden;
}
```

以上情况应用规则 计算BFC高度的时候浮动元素也会参与计算

2. #### 避免外边距折叠

当2个box在同一个BFC容器内，同时使用margin会引起外边距重合

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container{
            overflow: hidden;
        }
        .inner {
            margin: 10px 0;
            background: green;
            
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="inner">div1</div>
        <div class="inner">div2</div>
        <div class="inner">div3</div>
    </div>
</body>
</html>
```

此时将box变为BFC，增加如下样式：

```
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        .container{
            overflow: hidden;
        }
        .inner {
            margin: 10px 0;
            background: green;
            
        }
        .bfc {
            overflow: hidden;
        }
    </style>
</head>
<body>
    <div class="container">
        <div class="inner">div1</div>
        <div class="bfc">
            <div class="inner">div2</div>
        </div>
        
        <div class="inner">div3</div>
    </div>
</body>
</html>
```

以上情况应用规则 Box垂直方向的距离由margin决定。属于同一个BFC的两个相邻Box的margin会发生重叠

3. #### 自适应两栏布局

根据规则BFC的区域不会与浮动元素的box重叠，可以实现自适应两栏布局

```html
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
       .left{
        width: 500px;
        height: 150px;
        float: left;
        background: rgb(139, 214, 78);
        text-align: center;
        line-height: 150px;
        font-size: 20px;
       }
       .right{
        overflow: hidden;
        height: 300px;
        background: rgb(170, 54, 236);
        text-align: center;
        line-height: 300px;
        font-size: 40px;
       }
    </style>
</head>
<body>
   <div class="left"></div>
   <div class="right"></div>
</body>
</html>
```

BFC就是页面上的一个隔离的独立容器，容器里面的子元素不会影响到外面的元素。反之也如此。

##### JavaScript对象的底层数据结构是什么

JavaScript基本类型数据都是直接按值存储在栈中的(Undefined、Null、不是new出来的布尔、数字和字符串)，每种类型的数据占用的内存空间的大小是确定的，并由系统自动分配和自动释放。这样带来的好处就是，内存可以及时得到回收，相对于堆来说 ，更加容易管理内存空间。

JavaScript引用类型数据被存储于堆中 (如对象、数组、函数等，它们是通过拷贝和new出来的）。其实，说存储于堆中，也不太准确，因为，引用类型的数据的地址指针是存储于栈中的，当我们想要访问引用类型的值的时候，需要先从栈中获得对象的地址指针，然后，在通过地址指针找到堆中的所需要的数据。



##### Symbol类型在实际开发中的应用、可手动实现一个简单的Symbol

1. 使用Symbol来替代常量

2. 使用Symbol来作为对象属性名(key)

   ```js
   const PROP_NAME = Symbol()
   const PROP_AGE = Symbol()
   let obj = {
     [PROP_NAME]: "一斤代码"
   }
   obj[PROP_AGE] = 18
   ```

3. 使用Symbol定义类的私有属性/方法

   ```js
   // a.js
   const PASSWORD = Symbol()
   class Login {
     constructor(username, password) {
       this.username = username
       this[PASSWORD] = password
     }
   
     checkPassword(pwd) {
         return this[PASSWORD] === pwd
     }
   }
   export default Login
   // b.js
   import Login from './a'
   const login = new Login('admin', '123456')
   login.checkPassword('123456')  // true
   login.PASSWORD  // oh!no!
   login[PASSWORD] // oh!no!
   login["PASSWORD"] // oh!no!
   ```

   注册和获取全局Symbol window中创建的Symbol实例总是唯一的，而我们需要的是在所有这些window环境下保持一个共享的Symbol。这种情况下，我们就需要使用另一个API来创建或获取Symbol，那就是Symbol.for()，它可以注册或获取一个window间全局的Symbol实例

   

4. 注册和获取全局Symbol window中创建的Symbol实例总是唯一的，而我们需要的是在所有这些window环境下保持一个共享的Symbol。这种情况下，我们就需要使用另一个API来创建或获取Symbol，那就是Symbol.for()，它可以注册或获取一个window间全局的Symbol实例

   ```js
   let gs1 = Symbol.for('global_symbol_1')  //注册一个全局Symbol
   let gs2 = Symbol.for('global_symbol_1')  //获取全局Symbol
   gs1 === gs2  // true
   ```

   

##### JavaScript中的变量在内存中的具体存储形式

引用类型是保存在堆内存中的对象，值大小不固定，栈内存中存放的该对象的访问地址指向堆内存中的对象，JavaScript不允许直接访问堆内存中的位置，因此操作对象时，实际操作对象的引用

```js
let a1 = 0; // 栈内存
let a2 = "this is string" // 栈内存
let a3 = null; // 栈内存
let b = { x: 10 }; // 变量b存在于栈中，{ x: 10 }作为对象存在于堆中
let c = [1, 2, 3]; // 变量c存在于栈中，[1, 2, 3]作为对象存在于堆中
```



##### 基本类型对应的内置对象，以及他们之间的装箱拆箱操作

**内置对象：** Object是 JavaScript 中所有对象的父对象 数据封装类对象：Object、Array、Boolean、Number 和 String 其他对象：Function、Math、Date、RegExp、Error。 特殊的基本包装类型(String、Number、Boolean) arguments: 只存在于函数内部的一个类数组对象

**装箱：** 把基本数据类型转化为对应的引用数据类型的操作，装箱分为隐式装箱和显示装箱 

**隐式装箱**:

```js
let a = 'sun'
let b = a.indexof('s') // 0 // 返回下标

// 上面代码在后台实际的步骤为：
let a = new String('sun')
let b = a.indexof('s')
a = null

// 实现机制：
/**
 *	1.创建String类型的一个实例； 2.在实例上调用指定的方法； 3.销毁这个实例；
 */
```

**显示装箱**: 通过内置对象可以对Boolean、Object、String等可以对基本类型显示装箱 let a = new String('sun')

**拆箱：** 拆箱和装箱相反，就是把引用类型转化为基本类型的数据，通常通过引用类型的valueof()和toString（）方法实现

```js
let name = new String('sun')
let age = new Number(24)
console.log(typeof name) // object
console.log(typeof age) //  object
// 拆箱操作
console.log(typeof age.valueOf()); // number // 24  基本的数字类型
console.log(typeof name.valueOf()); // string  // 'sun' 基本的字符类型
console.log(typeof age.toString()); // string  // '24' 基本的字符类型
console.log(typeof name.toString()); // string  // 'sun' 基本的字符类型
```

##### 作用域和闭包

**理解词法作用域和动态作用域**：

**词法作用域**，函数的作用域在函数定义的时候就决定了（取决于函数定义的位置）
**动态作用域**，函数的作用域在函数调用的时候就决定了（取决于函数的调用） js采用的是词法作用域

**理解JavaScript的作用域和作用域链**：

作用域就是一个独立的地盘，让变量不会外泄、暴露出去。也就是说作用域最大的用处就是隔离变量，不同作用域下同名变量不会有冲突。 ES6 之前 JavaScript 没有块级作用域,只有全局作用域和函数作用域。ES6的到来，为我们提供了‘块级作用域’,可通过新增命令let和const来体现。

**作用域链** 在 JavaScript 中使用变量时，JavaScript 引擎将尝试在当前作用域中查找变量的值。如果找不到变量，它将查找外部作用域并继续这样做，直到找到变量或到达全局作用域为止。

如果仍然找不到变量，它将在全局作用域内隐式声明变量（如果不是在严格模式下）或返回错误。 ####3.理解JavaScript的执行上下文栈，可以应用堆栈信息快速定位问题 执行上下文是当前 JavaScript 代码被解析和执行时所在环境的抽象概念。

**执行上下文的类型** 执行上下文总共有三种类型
 **全局执行上下文**：只有一个，浏览器中的全局对象就是 window 对象，this 指向这个全局对象。
 **函数执行上下文**：存在无数个，只有在函数被调用的时候才会被创建，每次调用函数都会创建一个新的执行上下文。
 **Eval 函数执行上下文**： 指的是运行在 eval 函数中的代码，很少用而且不建议使用。

**执行栈** 执行栈，也叫调用栈，具有 LIFO（后进先出）结构，用于存储在代码执行期间创建的所有执行上下文。 首次运行JS代码时，会创建一个全局执行上下文并Push到当前的执行栈中。每当发生函数调用，引擎都会为该函数创建一个新的函数执行上下文并Push到当前执行栈的栈顶。 根据执行栈LIFO规则，当栈顶函数运行完成后，其对应的函数执行上下文将会从执行栈中Pop出，上下文控制权将移到当前执行栈的下一个执行上下文。

**执行上下文的创建** 执行上下文分两个阶段创建：
 1）创建阶段；
 2）执行阶段
 **创建阶段**
 1、确定 this 的值，也被称为 This Binding。
 2、LexicalEnvironment（词法环境） 组件被创建。
 3、VariableEnvironment（变量环境） 组件被创建。
 **This Binding:**
 在全局执行上下文中，this 的值指向全局对象，在浏览器中，this 的值指向 window 对象。 在函数执行上下文中，this 的值取决于函数的调用方式。如果它被一个对象引用调用，那么 this 的值被设置为该对象，否则 this 的值被设置为全局对象或 undefined（严格模式下）

**词法环境**
 在词法环境中，有两个组成部分：
（1）环境记录（environment record）
 （2）对外部环境的引用 环境记录是存储变量和函数声明的实际位置。 对外部环境的引用意味着它可以访问其外部词法环境。
 **变量环境:**
 它也是一个词法环境，其 EnvironmentRecord 包含了由  VariableStatements 在此执行上下文创建的绑定。 如上所述，变量环境也是一个词法环境，因此它具有上面定义的词法环境的所有属性。 在 ES6 中，LexicalEnvironment 组件和 VariableEnvironment 组件的区别在于前者用于存储函数声明和变量（ let 和 const ）绑定，而后者仅用于存储变量（ var ）绑定。 在创建阶段，代码会被扫描并解析变量和函数声明，其中函数声明存储在环境中，而变量会被设置为 undefined（在 var 的情况下）或保持未初始化（在 let 和 const 的情况下） 这就是为什么你可以在声明之前访问 var 定义的变量（尽管是 undefined ），但如果在声明之前访问 let 和 const 定义的变量就会提示引用错误的原因。

这就是我们所谓的变量提升。

#####介绍下 Set、Map、WeakSet 和 WeakMap 的区别？

**WeakSet 结构与 Set 类似，也是不重复的值的集合。但是，它与 Set 有两个区别。**

- WeakSet 的成员只能是对象，而不能是其他类型的值
- WeakSet 中的对象都是弱引用，即垃圾回收机制不考虑 WeakSet 对该对象的引用，也就是说，如果其他对象都不再引用该对象，那么垃圾回收机制会自动回收该对象所占用的内存，不考虑该对象还存在于 WeakSet 之中

**WeakMap结构与Map结构类似，也是用于生成键值对的集合**

- WeakMap只接受对象作为键名（null除外），不接受其他类型的值作为键名
- WeakMap的键名所指向的对象，不计入垃圾回收机制











