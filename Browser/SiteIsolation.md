# Site Isolation for web developers



- it ensures that pages from different websites are always put into different processes, each running in a sandbox that limits what the process is allowed to do
- blocks the process from receiving certain types of sensitive data from other sites.



Even when all cross-site pages are put into separate processes, pages can still legitimately request some cross-site subresources, such as images and JavaScript. A malicious web page could use an `<img>` element to load a JSON file with sensitive data, like your bank balance:

```html
<img src="https://your-bank.example/balance.json" />
<!-- Note: the attacker refused to add an `alt` attribute, for extra evil points. -->
```

Without Site Isolation, the contents of the JSON file would make it to the memory of the renderer process, at which point the renderer notices that it’s not a valid image format and doesn’t render an image. But, the attacker could then exploit a vulnerability like Spectre to potentially read that chunk of memory.

Cross-Origin Read Blocking, or CORB, is a new security feature that prevents the contents of `balance.json` from ever entering the memory of the renderer process memory based on its MIME type.



Websites can request two types of resources from a server:

- Data resources such as HTML, XML or JSON documents
- media resources such as images, JavaScript, CSS or fonts

A website is able to receive *data resources* from its own origin or from other origins with permissive [CORS](https://developer.mozilla.org/docs/Web/HTTP/CORS) headers such as `Access-Control-Allow-Origin: *`. On the other hand, *media resources* can be included from any origin, even without permissive CORS headers.



CORB (Cross-Origin Read Blocking) prevents the renderer process from receiving a cross-origin data resource (i.e. HTML, XML, or JSON) if:

- the resource has an `X-Content-Type-Options: nosniff` header
- CORS doesn’t explicitly allow access to the resource

Data resources that are blocked by the CORB policy are presented to the process as empty, although the request does still happen in the background. As a result, a malicious web page has a hard time pulling cross-site data into its process to steal.



##### Site Isolation side-effect

**Full-page layout is no longer synchronous**: Since the frames of a page may now be spread across multiple processes. This might affect pages if they assume that a layout change immediately propagates to all frames on the page.

If a page changes the size of a cross-origin `<iframe>` and then sends a `postMessage` to it, with Site Isolation the receiving frame may not yet know its new size when receiving the message. More generally, this might break pages if they assume that a layout change immediately propagates to all frames on the page.



**Unload handlers might time out more often**:























