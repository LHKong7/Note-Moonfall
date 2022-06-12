# JavaScript

### Runtime concepts

##### The event loop

JavaScript has a runtime model based on an event loop, which is responsible for executing the code, collecting and processing events, and executing queued sub-tasks. 



**Stack**: Function calls form a stack of *frames*.

**Heap**: Objects are allocated in a heap which is just a name to denote a large (mostly unstructured) region of memory.

**Queue**: A JavaScript runtime uses a message queue, which is a list of messages to be processed. Each message has an associated function that gets called to handle the message.



**Event Loop**:



**Run-to-completion**: Each message is processed completely before any other message is processed.

A downside of this model is that if a message takes too long to complete, the web application is unable to process user interactions like click or scroll. The browser mitigates this with the "a script is taking too long to run" dialog. A good practice to follow is to make message processing short and if possible cut down one message into several messages.



**Adding messages**: In web browsers, messages are added anytime an event occurs and there is an event listener attached to it. If there is no listener, the event is lost. So a click on an element with a click event handler will add a message—likewise with any other event.

**Zero delays**: Zero delay doesn't mean the call back will fire-off after zero milliseconds. Calling [`setTimeout`](https://developer.mozilla.org/en-US/docs/Web/API/setTimeout) with a delay of `0` (zero) milliseconds doesn't execute the callback function after the given interval.

**Serveral runtimes communicating together**

A web worker or a cross-origin `iframe` has its own stack, heap, and message queue. Two distinct runtimes can only communicate through sending messages via the [`postMessage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage) method. This method adds a message to the other runtime if the latter listens to `message` events.

**Never Blocking**: 

A very interesting property of the event loop model is that JavaScript, unlike a lot of other languages, never blocks. Handling I/O is typically performed via events and callbacks, so when the application is waiting for an [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API) query to return or an [XHR](https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest) request to return, it can still process other things like user input.



# Redux

##### Core Concepts

**Actions**: An actrion is a plain JavaScript object that has a `type` field. (thinking as an event that describes something that happened in the applications).

The `type` gives this action a descritpive name. -> `domain/eventName`

An action object can have other fields with additional information about what happened. By convention, we put that information in a field called `payload`.

```js
const addTodoAction = {
  type: 'todos/todoAdded',
  payload: 'Buy milk'
}
```



**Action Creator**: An **action creator** is a function that creates and returns an action object.

```js
const addTodo = text => {
  return {
    type: 'todos/todoAdded',
    payload: text
  }
}
```

**Reducers**: A **reducer** is a function that receives the current `state` and an `action` object, decides how to update the state if necessary, and returns the new state: `(state, action) => newState`.  (Think as an event listener which handles events based on the received action (event) type.)



**Store**: The current Redux application state lives in an object called the **store**. The store is created by passing in a reducer, and has a method called `getState` that returns the current state value.

The store is created by passing in a reducer, and has a method called `getState` that returns the current state value:



**Dispatch**: The Redux store has a method called `dispatch`. **The only way to update the state is to call `store.dispatch()` and pass in an action object**.

(he store will run its reducer function and save the new state value inside, and we can call `getState()` to retrieve the updated value)



**Selectors**:

**Selectors** are functions that know how to extract specific pieces of information from a store state value.







### Redux Toolkit



**createAction**(type, prepareAction?):  generates an action creator function for the given action type string. The function itself has `toString()` defined, so that it can be used in place of the type constant.





# Golang







# 3/29



### Request Pool





##### Web Worker





##### Network Request Exception





# 3/30



##### ES Module

**Import**: static `import` statement is used to import read only live bindings where are exported by another module.

Import can be used in embedded scripts by having a `type='module'`. Bindings imported are called live bindings because they are updated by the module that export the binding

**Import a module for its side effects only**: Import an entire module for side effects only, without importing anything. This runs the module's global code, but doesn't actually import any values.

**Importing defaults**: It is possible to have a default [`export`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export) (whether it is an object, a function, a class, etc.). The `import` statement may then be used to import such defaults.



Dynamic Import:

```js
(async () => {
  if (somethingIsTrue) {
    const { default: myDefault, foo, bar } = await import('/modules/my-module.js');
  }
})();
```

Why?

- When importing statically significantly slows the loading of your code and there is a low likelihood that you will need the code you are importing, or you will not need it until a later time.
- When importing statically significantly increases your program's memory usage and there is a low likelihood that you will need the code you are importing.
- When the module you are importing does not exist at load time
- When the import specifier string needs to be constructed dynamically. (Static import only supports static specifiers.)
- When the module being imported has side effects, and you do not want those side effects unless some condition is true. (It is recommended not to have any side effects in a module, but you sometimes cannot control this in your module dependencies.)



**Tree Shaking**:  a term commonly used within a JavaScript context to describe the rmeoval of dead code.

It relies on the `import` and `export` statements to detect if code modules are exported and imported fro use between JavaScript files.

> In moder JS application, webopack is used to remove dead code when bundling multiple JavaScript files into single files.



##### TypeScript:  .d.ts

Namespaces in Module Code:

```js
// This represents the JavaScript class which would be available at runtime
export class API {
  constructor(baseURL: string);
  getInfo(opts: API.InfoRequest): API.InfoResponse;
}
// This namespace is merged with the API class and allows for consumers, and this file
// to have types which are nested away in their own sections.
declare namespace API {
  export interface InfoRequest {
    id: string;
  }
  export interface InfoResponse {
    width: number;
    height: number;
  }
}
```



##### Generics

Creating reusable components is *generics*, being able to create a. compnent that can work over a variety of types rather than a single one.





##### Function Type



# 3/31



#### Golang

##### Context

Package context defines the Contex type, which carries:

- deadlines
- cancellation signals
- other request-scoped values across API boundaries and between processes

When the parent context get cancelled, all contexts derived from it are also canceled.

Context should be passed explicitly



# 4/1

### Go并发：

##### Introduction：

协程：

​	独立的栈空间，共享堆空间，调度由用户自己控制，

线程：

​	一个线程上可以跑多个协程



并发主要由切换时间片来实现”同时”运行，并行则是直接利用多核实现多线程的运行，go可以设置使用核数，以发挥多核计算机的能力。



一个goroutine的栈在其生命周期开始时只有很小的栈（典型情况下2KB）

##### goroutine 调度：

**GMP**：

- G很好理解，就是个goroutine的，里面除了存放本goroutine信息外 还有与所在P的绑定等信息。
- P管理着一组goroutine队列，P里面会存储当前goroutine运行的上下文环境（函数指针，堆栈地址及地址边界），P会对自己管理的goroutine队列做一些调度（比如把占用CPU时间较长的goroutine暂停、运行后续的goroutine等等）当自己的队列消费完了就去全局队列里取，如果全局队列里也消费完了会去其他P的队列里抢任务。
- M（machine）是Go运行时（runtime）对操作系统内核线程的虚拟， M与内核线程一般是一一映射的关系， 一个groutine最终是要放到M上执行的；

P与M一般也是一一对应的。他们关系是： P管理着一组G挂载在M上运行。当一个G长久阻塞在一个M上时，runtime会新建一个M，阻塞G所在的P会把其他的G 挂载在新建的M上。当旧的G阻塞完成或者认为其已经死掉时 回收旧的M。





# 4/2

##### Go SQL 数据库

`sql.DB` : 不是数据库连接。没有映射到任何特定的数据库软件中的数据库或模式的概念。

`sql.DB` 会在后台解决一些重要任务：

- 它通过驱动程序打开和关闭与实际底层数据库的连接
- 它根据需要管理连接池，这可能是前面提到的各种各样的东西

`sql.DB` 抽象 : 在使您不必担心如何管理对底层数据存储的并发访问。当您使用连接来执行任务时，该连接会被标记为使用中，然后在不再使用时返回到可用池中。这样做的一个后果是，**如果您无法将连接释放回池，则可能导致`sql.DB` 打开大量连接**，这可能会耗尽资源(连接太多，打开文件句柄过多，缺少可用的网络端口等)。稍后我们将详细讨论。



有几种常用的操作可以从数据库中检索结果:

- 执行返回一条数据的查询操作
- 准备要重复使用的语句，在多次执行该语句后进行销毁
- 一次性的执行语句，并且不打算将其重复使用
- 执行返回一条数据的查询，这种特殊情况有一个快捷方式



Go 的 `database/sql` 包中函数名称很重要。**如果一个函数名字包含 `Query`, 那么该函数旨在向数据库发出查询问题, 并且即使它为空，也将返回一组行**。不返回行的语句不应该使用 `Query` 函数; 而应使用 `Exec()`。

# 4/6



**TypeScript**:

**never**: 

​		Some functions never return a value. In a return type, this means that the function throws an exception or terminates execution of the program.

​		The `never` type represents values which are never observed. 

​		`never` also appears when TypeScript determines there's nothing left in a union	

**Function**: 

​		The global type `Function` describes properties like `bind, call, apply` and other present on all function values in JavaScript. 

​		This is an *untyped function call* and is generally best avoided because of the unsafe `any` return type.

​		If you need to accept an arbitrary function but don’t intend to call it, the type `() => void` is generally safer.

**void**:

​		 represents the return value  of functions which don't return a value. It is the inferred type any time a function doesn't have any `return` statement, or doesn't return any explicit value from those return statements.

**object**:

​		The special type `object` refers to any value that isn’t a primitive (`string`, `number`, `bigint`, `boolean`, `symbol`, `null`, or `undefined`). This is different from the *empty object type* `{ }`, and also different from the global type `Object`. It’s very likely you will never use `Object`.

​		Note that in JavaScript, function values are objects: They have properties, have `Object.prototype` in their prototype chain, are `instanceof Object`, you can call `Object.keys` on them, and so on. For this reason, function types are considered to be `object`s in TypeScript.





# 4/7



##### React LifeCycle Method:

`static getDerivedStateFromProps()` : is invoked right before calling the render method, both on initial mount and on subsequent updates. It should return an object to update the state or `null` to update nothing.

This method exists for [rare use cases](https://reactjs.org/blog/2018/06/07/you-probably-dont-need-derived-state.html#when-to-use-derived-state) where the state depends on changes in props over time. For example, it might be handy for implementing a `<Transition>` component that compares its previous and next children to decide which of them to animate in and out.

### Animations

Modern browsers c an animate two CSS properties cheaply: `transform` and. `opacity`.

60 FPS is the target when animating anything on the web.

On the web, a frame is the time that it takes to do all of the work required to update and repaint the screen. If each frame does not complete within 16.7ms (1000ms / 60  = 16.7), then users will perceive the delay.

**rendering pipeline**:

1. Styles: Calculate the styles that apply to the elements

2. Layout: Generate the geometry and position for each element

3. Paint: Fill out the pixels for each elements into layers

   ​	**Layers**: 

4. Composite: Draw the layers to the screen

The rendering pipeline is running sequentially, Animating something that changes layout is therefore more expensive than animating. something that only changes compositing



##### More depth into rendering in modern browsers:

**Server to Client**:

**HSTS (Strict-Transport-Security)**: 

​		The HTTP response header informs browsers that the site should only be accesssed using HTTPS, and that any future attempts to access it using HTTP should automatically be converted to HTTPS

> **Note:** This is more secure than simply configuring a HTTP to HTTPS (301) redirect on your server, where the initial HTTP connection is still vulnerable to a man-in-the-middle attack.

`max-age=<expire-time>`: The time, in seconds, that the browser should remember that a site is only to be accessed using HTTPS.

The HTTP Strict Transport Security header informs the browser that it should never load a site using HTTP and should automatically convert all attempts to access the site using HTTP to HTTPS requests instead.



1. Check for HSTS:

   ​	If the requested HTTP host is in the HSTS list, a request is made to the HTTPS version of the URL instead of HTTP. 

2. Check for Service Workers

   ​	Browser needs to determine if a service worker is available to handle the request -- this is espically important in the case that the user is offline and does not have a network connection.

   ​	A service worker can be registered when a page is visited, a process that records the service worker resgistration and URL mapping to a local database. If a service worker exists for that given URL, it will be allowed to handle responding to the request. 

   ​	

   In case of there is no service workers to handle the intiial request (or if Navigation preload is being used), the browser moves on to consulting the networking layer.

3. Check the Network Cache

   ​	The browser, via the network layer, will check if there's a fresh response in its cache. This is usually defined by the `Cache-Control` header in the response,

   ​		`max-age` : can define how long the cached item is considered fresh

   ​		`no-store` : indicates whether it should be cached at all. And of course, if the browser finds nothing in its network cache, then a network request will be required. If there is a fresh response in the cache, it is returned back for the purpose of loading the page.

   ​		`If-Modified-Since` or `If-None-Match` header that tells the server that version of the content the browser already has in its cache. 

   ​			Server either tell the browser that its copy is still fresh by returing an `HTTP 304 (Not Modified)` with no body, or tell the browser that its copy is stale by returning an `HTTP 200 (OK)` response with the new version of the resource.

4. Check for Connection

   ​	If there is previously established connection for the host and port for the request, the connection will be reused rather than establishing a new one. 

   ​	If not, the browser consults the networking. layer to understand if it. needs to do a DNS lookup.

   ​	**DNS LookUp**:

   - looking  through the local DNS cache (which is stored on device), depending on the freshness of that cache, remote name servers may also be consulted (they can be hosted by ISP) which would eventually result in the correct IP address for browser to connect to.
   - In some cases, the browser may be able to predict which domains will be accessed, and connections to those domains can be primed. The resource can hint to the browser which to prime conenctions to by using resource hint 

5. Establish Connection

   ​	Establish a connection with the server so the server knows it will be both sending to and receiving from the client. 

   ​		TLS:  perform a TLS handshake to validate the certificate provided by the server

6. Send the request to the server

   ​	The first request that will go over this connection is the top-level page request. Typically this will be an HTML file that get served from the server back to the client.

7. Handle the response

   ​	AS the data is being streamed over the client, the response data is analyzed.

   ​			a. the browser checks the headers of the response, HTTP headers are name-value pairs that are sent as part of the HTTP response. 

   ​			If the headers of the response indicate a redirect, the browser starts the navigfation process all over again and returns to the very first step of checking if an HSTS upgrade is required. 

   ​			

   ​			If the server response is compressed or chunked, the browser will attempt to decompress and dechunk it.

   ​		

   ​			As the response is being read, the browser will also kick off writing it to the network cache in parallel.

   ​			the browser will attempt to understand the MIME type of the file being sent to the browser, so it can appropriately interpret how to load the file. 

By this point, the requested navigation URL has been entered into the browser history, which makes it available for navigation in the back and forward functionality of the browser.



***Caching***: the network cache is programmatic cahces that can be leverged via JavaScript.

**Tags to DOM**:

**Parsing**:

​		HTML parser: is composed of a few system working together: encoding, pre-parsing, tokenization and tree construction.

**Encoding**:

​		The payload of an HTTP response body can be anything from HTML text to image data. The first job of the parser is to figure out how to interpret the bits just received from the server. The server will provide hints via `content-type` headers.

The decoder must figure out how the text document was translated into bits in order to reverse the. process.

When saving your HTML documents for the web today, the choice is clear: use UTF-8 encoding. Why? It nicely supports the full Unicode range of characters, has good compatibility with ASCII for single-byte characters common to languages like CSS, HTML, and JavaScript, and is likely to be the browser’s fallback default.



**Pre-parsing/scanning**:

Once the encoding is known, the parser starts an initial pre-parsing step to scan the content with the goal of minimizing round-trip latency for additional resources. 

The pre-parser does recognize specific HTML tag names and attributes, as well as URLs. For example, if you have an `<img src="https://somewhere.example.com/images/dog.png" alt="">` somewhere in your HTML content, the pre-parser will notice the `src` attribute, and queue a resource request for the dog picture via the networking system.

The pre-parser may also notice certain explicit requests in the HTML such as [preload](https://developer.mozilla.org/en-US/docs/Web/HTML/Preloading_content) and [prefetch directives](https://developer.mozilla.org/en-US/docs/Web/HTTP/Link_prefetching_FAQ), and queue these up for processing as well.

**Parsing**:

​		**Tokenization**: Tokenization involves turning the markup into individual tokens such as `begin tag, end tag, text run, comment and so forth`.  The tokenizer is a state machine that transitions between the different states of the HTML language, such as "in tag open state". 

For those who perfer a more black-and-white approach to markup language correctness, browsers have an alternate parsing mechanism built in that treats any failure as a catastrophic failure (meaning any failure will cause the content to not render). 

​		This parsing mode uses the [rules of XML to process HTML](https://en.wikipedia.org/wiki/XHTML), and can be enabled by sending the document to the browser with the “application/xhtml+xml” [MIME type](https://en.wikipedia.org/wiki/MIME) 

Browsers may combine the pre-parser and tokenization steps together as an optimization.

**Parsing/tree construction**:

​		The browser needs an internal (in-memory) representation of a web page, in the DOM standard, web standards define exactly what shape that representation should be.

​		The parser's responsibility is to take the tokens create and insert the objects into the Document Object Model (DOM) in the appropriate way.

​		Using JavaScript, a web page can rearrage the DOM tree in almost any way it likes, even if it does not make sense. JavaScript can add more content to be parsed while the parser is in the middle of doing its job. `<script>` tags contain text that the parser must collect and then send to a scripting engine for evaluation. While the script engine parses and evaluates the script text, the parser waits. If the script evaluation includes invoking the `document.write` API, a second intstance of the HTML parser must start running.  `<script>` and `document.write` require stopping all in-progress work to go back to the store to get some additional materials that we hadn’t realized we needed. While we’re away at the store, all progress on the construction is stalled.



**Events**:

When the parser finishes, it announces its completion via an event called `DOMContentLoaded`. 

Events are the broadcast system built into the browser that JavaScript can listen and respond to; Events are the reports that various workers bring to the foreman when they encounter a problem or finish a task

The browser creates an event object in the DOM, packs it full of useful state information (such as the location of the touch on the screen), and "fires" that event.

The tree structure of the DOM makes it convenient to “filter” how frequently code responds to an event by allowing events to be listened for at any level in the tree (i.e.., at the root of the tree, in the leaves of the tree, or anywhere in between).

he browser first determines where to fire the event in the tree (meaning which DOM object, such as a specific `<input>` control), and then calculates a route for the event starting from the root of the tree, then down each branch until it reaches the target (the `<input>` for example), and then back along the same path to the root. Each object along the route then has its event listeners triggered, so that listeners at the root of the tree will “see” more events than specific listeners at the leaves of the tree.

Some events can also be canceled, which provides, for example, the ability to stop a form submission if the form isn’t filled out properly. (A `submit` event is fired from a `<form>` element, and a JavaScript listener can check the form and optionally cancel the event if fields are empty or invalid.)



**DOM**:



**Element Interfaces**:

As the parser is constructing objects to put into the tree, it looks up the element’s name (and namespace) and finds a matching HTML interface to wrap around the object.

Interfaces add features to basic HTML elements that are specific to their *kind* or *type* of element. Some generic features include:

- access to HTML collections representing all or a subset of the element’s children;
- the ability to search the element’s attributes, children, and parent elements;
- and importantly, ways to create new elements (without using the parser), and attach them to (or detach them from) the tree.



The scope of the browser’s DOM is comparable to the set of features that apps can use in any operating system. Things like (but not limited to):

- access to storage systems (databases, key/value storage, network cache storage);
- devices (geolocation, proximity and orientation sensors of various types, USB, MIDI, Bluetooth, Gamepads);
- the network (HTTP exchanges, bidirectional server sockets, real-time media streaming);
- graphics (2D and 3D graphics primitives, shaders, virtual and augmented reality);
- and multithreading (shared and dedicated execution environments with rich message passing capabilities).



##### Braces to Pixels

**Parsing**:

Once CSS is downloaded by the browser, the CSS parser is spun up to handle any CSS that it encounters. This can be CSS within individual documents, inside of `<style>` tags, or inline within the `style` attribute of a DOM element. At the end of this process, we have a data structure with all the selectors, properties, and properties’ respective values.

One thing that is worth noting is that the browser exploded the shorthands of `background` and `border` into their longhand variants, as shorthands are primarily for developer ergonomics; the browser only deals with the longhands from here on.

*Computation*:

| Web Developer                   | Computed Value             |
| :------------------------------ | :------------------------- |
| `font-size: 1em`                | `font-size: 16px`          |
| `width: 50%`                    | `width: 50%`               |
| `height: auto`                  | `height: auto`             |
| `width: 506.4567894321568px`    | `width: 506.46px`          |
| `line-height: calc(10px + 2em)` | `line-height: 42px`        |
| `border-color: currentColor`    | `border-color: rgb(0,0,0)` |
| `height: 50vh`                  | `height: 540px`            |
| `display: grid`                 | `display: grid`            |



**Cascade**:

Since the CSS can come from a variety of sources, the browser needs a way to determine which styles should apply to a given element. To do this, the browser uses a formula called specificity

​		Specificity: counts the number of tags, classes, ids and attributes selectors utilized in the selector, as well as the number of `!important` declarations present. 

Styles on an element via the inline `style` attribute are given a rank that wins over any style from within a `<style>` block or external style sheet.

| Selector                  | Specificity Score |
| :------------------------ | :---------------- |
| `li`                      | `0 0 0 0 1`       |
| `li.foo`                  | `0 0 0 1 1`       |
| `#comment li.foo.bar`     | `0 0 1 2 1`       |
| `<li style="color: red">` | `0 1 0 0 0`       |
| `color: red !important`   | `1 0 0 0 0`       |

So what does the engine do when the specificity is tied? Given two or more selectors of equal specificity, the winner will be whichever one appears last in the document



```css
.fancy-button {
	background: green;
	border: 3px solid red;
	font-size: 1em;
}

div .fancy-button {
	background: yellow;
}
```

| Selector            | Property           | Value            | Specificity Score | Document Order |
| :------------------ | :----------------- | :--------------- | :---------------- | :------------- |
| `.fancy-button`     | `background-color` | `rgb(0,255,0)`   | `0 0 0 1 0`       | `0`            |
| `.fancy-button`     | `border-width`     | `3px`            | `0 0 0 1 0`       | `1`            |
| `.fancy-button`     | `border-style`     | `solid`          | `0 0 0 1 0`       | `2`            |
| `.fancy-button`     | `border-color`     | `rgb(255,0,0)`   | `0 0 0 1 0`       | `3`            |
| `.fancy-button`     | `font-size`        | `16px`           | `0 0 0 1 0`       | `4`            |
| `div .fancy-button` | `background-color` | `rgb(255,255,0)` | `0 0 0 1 1`       | `5`            |



**Understanding Origins**:

In CSS, there are also origins, but they serve different purposes:

- user: any styles set globally within the user agent by the user;
- author: the web developer’s styles;
- and user agent: anything that can utilize and render CSS (to most web developers and users, this is a browser).

The cascade power of each of these origins ensures that the greatest power lies with the user, then the author, and finally the user agent.



When the browser has a complete data structure of all declarations from all origins, it will sort them in accordance with specification. First it will sort by origin, then by specificity, and finally, by document order.

| Origin ![⬆](https://s.w.org/images/core/emoji/13.1.0/svg/2b06.svg) | Selector            | Property           | Value            | Specificity Score ![⬆](https://s.w.org/images/core/emoji/13.1.0/svg/2b06.svg) | DocumentOrder ![⬇](https://s.w.org/images/core/emoji/13.1.0/svg/2b07.svg) |
| :----------------------------------------------------------- | :------------------ | :----------------- | :--------------- | :----------------------------------------------------------- | :----------------------------------------------------------- |
| `User`                                                       | `*`                 | `font-size`        | `32px`           | `0 0 0 0 1`                                                  | `0`                                                          |
| `Author`                                                     | `div .fancy-button` | `background-color` | `rgb(255,255,0)` | `0 0 0 1 1`                                                  | `5`                                                          |
| `Author`                                                     | `.fancy-button`     | `background-color` | `rgb(0,255,0)`   | `0 0 0 1 0`                                                  | `0`                                                          |
| `Author`                                                     | `.fancy-button`     | `border-width`     | `3px`            | `0 0 0 1 0`                                                  | `1`                                                          |
| `Author`                                                     | `.fancy-button`     | `border-style`     | `solid`          | `0 0 0 1 0`                                                  | `2`                                                          |
| `Author`                                                     | `.fancy-button`     | `border-color`     | `rgb(255,0,0)`   | `0 0 0 1 0`                                                  | `3`                                                          |
| `Author`                                                     | `.fancy-button`     | `font-size`        | `16px`           | `0 0 0 1 0`                                                  | `4`                                                          |



**Layout**:

This tree is present in all modern engines and is referred to as the box tree. In order to construct this tree, we traverse down the DOM tree and create zero or more CSS boxes, each having a margin, border, padding and content box.



In this section, we’ll be discussing the following CSS layout concepts:

- Formatting context (FC) : there are many types of formatting contexts, most of which web developers invoke by changing the `display` value for an element. Some of the most common formatting contexts are block (block formatting context, or BFC), flex, grid, table-cells and inline. Some other CSS can force a new formatting context, too, such as `position: absolute` using `float` or utilizing multi-column.
- Containing block: this is the ancestor block that you resolve styles against.
- Inline direction: this is the direction in which text is laid out, as dictated by the element’s writing mode.
- Block direction: this behaves exactly the same as the inline direction but is perpendicular to that axis.



`auto` , `percentage` or `pixel` . The purpose of layout is to size and position all the boxes in the box tree to get them ready for painting. 



**Dealing with Floats**: 

Float box are one type of box that matches this layout type, but there are many other boxes, such as absolute positioned boxes (including `position: fixed` elements) and table cells with `auto` -based sizing



**Understanding Fragmentation**:

One final aspect to touch on for how layout works is fragmentation. If you’ve ever printed a web page or used CSS Multi-column, then you’ve taken advantage of fragmentation. 

Fragmentation is the logic of breaking content apart to fit it into a different geometry. 





**Painting**:

Painting is roughly standardized by CSS, and to put it concisely (you can read the full breakdown in [CSS 2.2 Appendix E](https://www.w3.org/TR/CSS22/zindex.html#painting-order)), you paint in the following order:

- background;
- border;
- and content.



Once this is completed, it is converted to a bitmap. That’s right—ultimately every layout element (even text) becomes an image under the hood.


# 5/8
Object.freeze() : this method freezes an object. A frozen object can no longer be changed; freezing an object prevents new properties from being added to it, existing properties from being removed, prevents changing the enumerability, configurability or writability of existing properties, and prevents the values of existing properties from being changed. freeze() returns the same object that was passed in.

##### Content-security-Policy

