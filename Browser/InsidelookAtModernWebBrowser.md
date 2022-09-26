# Inside look at modern web browser



### Part 1:



**CPU (Center Processing Unit)**: 

**GPU (Graphics Processing Unit)**: Good at handling simple tasks but across multiple cores at tyhe same time.

**Process**: running application

**Thread**: one that lives inside of process and executes any part of its process's program



##### Browser Architecture

Current chrom architecture:

The top level is thr **browser process** which coordinating with other processes that take care of different parts of the application.

**Renderer process**: multiple processes are created and assigned to each tab. Recently, chrome gave each tab a process when it could; it tries to give each site its own process, including iframes



| process and what it controls                                 |
| :----------------------------------------------------------- |
| **Browser process**: controls "chrome" part of the application including address bar, bookmarks, back and forward buttons. Also handles the invisible, privileged parts of a web browser (network requests and file access) |
| **Renderer process**: Controls anything inside of the tab where a website is displayed |
| Plugin : any plugins used by the website such as, flash      |
| GPU process: Handles GPU tasks in isolation from other processes. It is separated into different process because GPUs handles requests from multiple apps and draw them in the same surface |



#### why multi-process architecture

1.  render isolation: If one tab becomes unresponsive, it will not affect other tabs. Otherwise, all tabs become unrepsonsive

2. Security and sandboxing: Since operating systems provide a way to restrict processes’ privileges, the browser can sandbox certain processes from certain features. For example, the Chrome browser restricts arbitrary file access for processes that handle arbitrary user input like the renderer process.

   Because processes have their own private memory space, they often contain copies of common infrastructure (like V8), 

   In order to solve the problem:

   ​	Chrome puts a limit on how many processes it can spin up. The limit varies depending on how much memory and CPU power your device has, but when Chrome hits the limit, it starts to run multiple tabs from the same site in one process.



Chrome is running on powerful hardware, it may split each service into different processes giving more stability, but if it is on a resource-constraint device, chrome consolidates services into one process saving memory footprint. (used on platform like Android)

##### Site Isolation (Since chrome 67)

Run a separatte renderer process for each cross-site iframe. Site Isolation isn’t as simple as assigning different renderer processes; it fundamentally changes the way iframes talk to each other.



## What happens in navigation



Everything outside of a tab is handled by the browser process. The browser process has threads like: 

- the UI thread which draws buttons and input fields of the browser, 
- network thread deals with network stack to receive data from the internet
- storage thread controls access to the files and more



When you type a URL into the address bar, the input is handled by browser process's UI thread.

**Simple Navigation**:

***STEP 1 Handling Input***

When a user starts to type into address bar, UI threads asks "us this a search query or URL". The UI thread needs to parse and decide whether to : 

- send you to a search engine, 
- or to the site you requested

***STEP 2 start navigation***

When user hits enter, UI thread initiates a network call to get site content. Loading spinner is displayed on the corner of a tab, and the network thread goes through appropriate protocols like DNS look up and establishing TLS Connection for the request.

At this point, the network thread may receive a server redirect header like **HTTP 301**. In that case, the network thread communicates with UI thread that the server is requesting redirect. Then, another URL request will be initiated.

***STEP 3 Read Response***

Once the response body (payload) starts to come in, the network thread looks at the first few bytes of the stream if necessary. The response's **Content-Type** header should say what type of data it is, but since it may be missing or wrong, `MIME Type sniffing` is done here.

If the response is the HTML file, then the next step would be to pass the data to the renderer process, but if it is a zip file or some other file then that means it is a download request so they need to pass the data to download manager. Then there are two security checks:

- SafeBrowing:  If the domain and the response data seems to match a known malicious site, then the network thread alerts to display a warning page.
- CORB : check happens in order to make sure sensitive cross-site data does not make it to the renderer process.

***STEP 4 Find a renderer process***

Once all of the checks are done and Network thread is confident that browser should navigate to the requested site, the Network thread tells UI thread that the data is ready. UI thread then finds a renderer process to carry on rendering of the web page.

Since the network request could take several hundred milliseconds to get a response back, an optimization to speed up this process is applied. When the UI thread is sending a URL request to the network thread at step 2, it already knows which site they are navigating to. The UI thread tries to proactively find or start a renderer process in parallel to the network request. This way, if all goes as expected, a renderer process is already in standby position when the network thread received data. This standby process might not get used if the navigation redirects cross-site, in which case a different process might be needed.



***STEP 5 Commit Navigation***

An IPC is sent from the browser process to the renderer process to commit the navigation. it also passes on the data stream so the renderer process can keep receiving HTML data. Once the browser process hears confirmation that the commit has happened in the renderer process, the navigation is complete and the document loading phase begins

At this point, address bar is updated and the security indicator and site settings UI reflects the site information of the new page. The session history for the tab will be updated so back/forward buttons will step through the site that was just navigated to. To facilitate tab/session restore when you close a tab or window, the session history is stored on disk.



***Extra STEP Initial load complete***

Once the renderer process "finishes" rendering, it sends an IPC back to the browser process (this is after all the `onload` events have fired on all frames in the page and have finished executing). At this point, the UI thread stops the loading spinner on the tab.



The simple navigation was complete! But what happens if a user puts different URL to address bar again? Well, the browser process goes through the same steps to navigate to the different site. But before it can do that, it needs to check with the currently rendered site if they care about [`beforeunload`](https://developer.mozilla.org/docs/Web/Events/beforeunload) event (create leavethissite alert when you try to navigate away or close the tab, Everything inside of a tab including JS code is handled by the renderer process) .



##### In case of Service Worker

Service worker is a way to write network proxy in the application code; allowing web developers to have more control over what to cache locally and when to get new data from the network. **If service worker is set to load the page from the cache, there is no need to request the data from the network**



Q: How does a browser process know the site has a service worker?

When a service worker is registered, the scope of the service worker is kept as a reference. When a navigation happens, network thread checks the domain against registered service worker scopes, if a service worker is resgistered for that URL, the UI thread finds a renderer process in order to execute the service worker code. The service worker may load data from cache, eliminating the need to request data from the network, or it may request new resources from the network.



##### Navigation preload

**a mechanism to speed up this process by loading resources in parallel to service worker startup. It marks these requests with a header, allowing servers to decide to send different content for these requests; for example, just updated data instead of a full document**



## Inner Workings of a Renderer Process

An general overview of renderer process

**Renderer processes handle web contents**

The renderer process is responsible for everything that happens inside of a tab.

In a renderer process:

- the main thread handles most of the code you send to user
- sometimes parts of the JS is handled by worker threads if you use a web worker or a service worker
- Compositor and raster thread are also run inside of a renderer process to render a page efficiently and smoothly

The renderer process's core job is to turn HTML, CSS, and JavaScript into a web page that the user can interact with.



#### Parsing

***Construction of a DOM***: 

When the renderer process receives a commit message for a navigation and starts tro receive HTML data, the main thread begins to parse the text string (HTML) and turn it into the Document Object Model (DOM)

The DOM is a browser's internal representation of the page as well as the data structure and API that web developer can interact with via JS



***Subresource loading***

A website usually uses external resources like images, CSS, and JavaScript. Those files need to be loaded from network or cache. The main thread *could* request them one by one as they find them while parsing to build a DOM, but in order to speed up, "preload scanner" is run concurrently. If there are things like `<img>` or `<link>` in the HTML document, preload scanner peeks at tokens generated by HTML parser and sends requests to the network thread in the browser process.



***JavaScript can block the parsing***

When the HTML parser finds a `<script>` tag, it pauses the parsing of the HTML document and has to load, parse and execute the JS code.

JavaScript can change the shape of the document using things like `document.write()` which changes the entire DOM structure ([overview of the parsing model](https://html.spec.whatwg.org/multipage/parsing.html#overview-of-the-parsing-model) in the HTML spec has a nice diagram). This is why the HTML parser has to wait for JavaScript to run before it can resume parsing of the HTML document.



***Hint to brwoser how you want to load resources***

If your JavaScript does not use `document.write()`, you can add [`async`](https://developer.mozilla.org/docs/Web/HTML/Element/script#attr-async) or [`defer`](https://developer.mozilla.org/docs/Web/HTML/Element/script#attr-defer) attribute to the `<script>` tag. The browser then loads and runs the JavaScript code asynchronously and does not block the parsing. 

You may also use [JavaScript module](https://developers.google.com/web/fundamentals/primers/modules) if that's suitable.

`<link rel="preload">` is a way to inform browser that the resource is definitely needed for current navigation and you would like to download as soon as possible



***Style Calculation***

The main thread parses CSS and determines the computed style for each DOM node. This is information about what kind of style is applied to each element based on CSS selectors. You can see this information in the `computed` section fo DevTools



***Layout***

The layout is a process to find the geometry of elements. The main thread walks through the DOM and computed styles and creates the layout tree which has infomration like x y coordinates and bounding box sizes.

 Layout tree may be similar structure to the DOM tree, but it only contains information related to what's visible on the page. 

> display:none -> the element is not part of the layout tree
>
> visible: hidden -> the element is in the layout tree
>
> Pseudo class p::before{content: "Hi!"} -> it is included in the layout tree even though that is not in the DOM

Determining the Layout of a page is a challenging task. Even the simplest page layout like a block flow from top to bottom has to consider how big the font is and where to line break them because those affect the size and shape of a paragraph; which then affects where the following paragraph needs to be.



CSS can make element float to one side, mask overflow item and change writing directions.



***Paint***

You know the size, shape and location of elements, but you still have to judge in what order you paint them. For example, `z-index` might be set for certain elements.

At the paint step, the main thread walks the layout tree to create paint records. Paint record is a note of painting process like `background first, then text, then rectangle`. 



***Updating rendering pipeline is costly***

The most important in rendering pipeline is that ***at each step the result of the previous operation is used to create new data. For example, if something changes in the layout tree, then the Paint order needs to be regenerated for affected parts of the document.

If you try to animate elements, the browser has to run these operations in between every frame. Most of the displays refresh the screen **60 times a second (60 fps)**;  Even if your rendering operations are keeping up with screen refresh, these calculations are running on the main thread, which means it could be blocked when your application is running JavaScript.

You can divide JavaScript operation into small chunks and schedule to run at every frame using `requestAnimationFrame()`. 

- Using `web worker` to avoid blocking the main thread



***Compositing***:

Rasterizing: turn the structure of document, style of each element, the geometry of the page and the paint order into pixels on the screen.

Compositing is a technique to separate parts of a page into layers, rasterize them separately, and composite as a page in a separate thread called compositor thread.

​	If scroll happens, since layers are already rasterized, all it has to do is to composite a new frame. Animation can be achieved in the same way by moving layers and composite a new frame.



***Dividig into layers***

In order to find out which elements need to be in which layers, the main thread walks through the layout tree to create the layer tree (this part is called "Update Layer Tree" in the DevTools performance panel). If certain parts of a page that should be separate layer (like slide-in side menu) is not getting one, then you can hint to the browser by using `will-change` attribute in CSS.



***Raster and composite off of the main thread***:

Once the layer tree is created and paint orders are determined, the main thread commits that information to the compositor thread. The compositor thread then rasterizes each layers. A layer could be large like the entire length of a page, , so the compositor thread divides them into tiles and sends each tile off to raster threads. Raster threads rasterize each tile and store them in GPU memory.

The compositor thread can prioritize different raster threads so that things within the viewport (or nearby) can be rastered first. A layer also has multiple tilings for different resolutions to handle things like zoom-in action.



Once tiles are rastered, compositor thread gathers tile information called **draw quads** to create a **compositor frame**.

| Draw quads       | Contains information such as the tile's location in memory and where in the page to draw the tile taking in consideration of the page compositing. |
| ---------------- | ------------------------------------------------------------ |
| Compositor frame | A collection of draw quads that represents a frame of a page. |

A compositor frame is then submitted to the browser process via IPC. At this point, another compositor frame could be added from UI thread for the browser UI change or from other renderer processes for extensions. These compositor frames are sent to the GPU to display it on a screen. If a scroll event comes in, compositor thread creates another compositor frame to be sent to the GPU.



The benefit of compositing is that it is done without involving the main thread. Compositor thread does not need to wait on style calculation or JavaScript execution. This is why [compositing only animations](https://www.html5rocks.com/en/tutorials/speed/high-performance-animations/) are considered the best for smooth performance. If layout or paint needs to be calculated again then the main thread has to be involved.



### Input is coming to the Compositor

input means any gesture from the user. Mouse wheel scroll is an input event and touch or mouse over is also an input event.



When user gesture like touch on a screen occurs, the browser process is the one that receives the gesture at first. However, the browser process is only aware of where that gesture occurred since content inside of a tab is handled by the renderer process. So the browser process sends the event type (like `touchstart`) and its coordinates to the renderer process. Renderer process handles the event appropriately by finding the event target and running event listeners that are attached.



##### Compositor receives input events

Since running JS is the main thread's job, 

when a page is composited, the compositor thread marks a region of the page that has event handlers attached as "Non-Fast Scrollable Region". By having this information, the compositor thread can make sure to send input event to the main thread if the event occurs in that region. If input event comes from outside of this region, then the compositor thread carries on compositing new frame without waiting for the main thread.

***Be aware when your write event handlers***

A common event handling pattern in web development is event delegation. Since events bubble, you can attach one event handler at the topmost element and delegate tasks based on event target. 

```js
document.body.addEventListener('touchstart', event => {
    if (event.target === area) {
        event.preventDefault();
    }
});
```

However, if you look at this code from the browser's point of view, now the entire page is marked as a non-fast scrollable region. This means even if your application doesn't care about input from certain parts of the page, the compositor thread has to communicate with the main thread and wait for it every time an input event comes in. Thus, the smooth scrolling ability of the compositor is defeated.

In order to mitigate this from happening, you can pass `passive: true` options in your event listener. This hints to the browser that you still want to listen to the event in the main thread, but compositor can go ahead and composite new frame as well.

```js
document.body.addEventListener('touchstart', event => {
    if (event.target === area) {
        event.preventDefault()
    }
 }, {passive: true});
```

***Check if the event is cancelable***

Using `passive: true` option in your pointer event means that the page scroll can be smooth, but vertical scroll might have started by the time you want to `preventDefault` in order to limit scroll direction. You can check against this by using `event.cancelable` method.

```js
document.body.addEventListener('pointermove', event => {
    if (event.cancelable) {
        event.preventDefault(); // block the native scroll
        /*
        *  do what you want the application to do here
        */
    }
}, {passive: true});
```

```css
// to completely eliminate the event handler.
#area {
  touch-action: pan-x;
}
```



***Finding the event target***

When the compositor thread sends an input event to the main thread, the first thing to run is a hit test to find the event target. Hit test uses paint records data that was generated in the rendering process to find out what is underneath the point coordinates in which the event occurred.

#####  Minimizing event dispatches to the main thread

If a continuous event like `touchmove` was sent to the main thread 120 times a second, then it might trigger excessive amount of hit tests and JavaScript execution compared to how slow the screen can refresh.



To minimize excessive calls to the main thread, Chrome coalesces continuous events (such as `wheel`, `mousewheel`, `mousemove`, `pointermove`, `touchmove` ) and delays dispatching until right before the next `requestAnimationFrame`.



Any discrete events like `keydown`, `keyup`, `mouseup`, `mousedown`, `touchstart`, and `touchend` are dispatched immediately.



##### Use `getCoalescedEvents` to get intra-frame events

For most web applications, coalesced events should be enough to provide a good user experience. However, if you are building things like drawing application and putting a path based on `touchmove` coordinates, you may lose in-between coordinates to draw a smooth line. In that case, you can use the `getCoalescedEvents` method in the pointer event to get information about those coalesced events.

```js
window.addEventListener('pointermove', event => {
    const events = event.getCoalescedEvents();
    for (let event of events) {
        const x = event.pageX;
        const y = event.pageY;
        // draw a line using x and y coordinates.
    }
});
```





