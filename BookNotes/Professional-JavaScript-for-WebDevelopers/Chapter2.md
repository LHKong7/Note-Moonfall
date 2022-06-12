# JavaScript in HTML

`<script>` Element: The primary method of inserting JavaScript into an HTML page is via <script> element. There are six attributes for the element:

- `async` → Indicates that the script should begin downloading immediately but should not prevent other actions on the page such as downloading resources or waiting for other scripts to load. Valid only for external script files.
- `charset` → The character set of the code specified using the src attribute
- `crossorigin` → Configures the CORS settings for the associated request; by default, CORS is not used at all. crossorigin="anonymous" will configure the request for the file to not have the credentials flag set. crossorigin="use-credentials" will set the credentials flag, meaning the outgoing request will include credentials.
- `defer` → Indicates that the execution of the script can safely be deferred until after the document’s content has been completely parsed and displayed. Valid only for external scripts.
- `integrity`: Allows for verification of Subresource Integrity (SRI) by checking the retrieved resource against a provided cryptographic signature. If the signature of the retrieved resource does not match that specified by this attribute, the page will error and the script will not execute. This is useful for ensuring that a Content Delivery Network (CDN) is not serving malicious payloads.
- `src` : Indicates an external file that contains code to be executed.
- `type` : replaces `language`; indicates the content type (also called MIME type) of the scripting language being used by the code block. If the value is `module` , the code is treated as an ES6 module and only then is eligible to use the `import` and `export` keywords.



There are two ways to use the `<script>` element:

1. embed JavaScript code directly into the page
2. include JavaScript from an external file



`<script>` can include JavaScript files from outside domain. Much like an `<img>` element, the `<script> `element's `src` attribute may be set to a full URL that exists outside the domain on which the HTML page exists.



When the browser goes to resolve this resource, it will send a `GET` request to the path specificed in the src attribute to retrieve the resource.



**Tag Placement**: 

including JS files inthe `<head>` of a document means that all of the JavaScript code must be downloaded, parsed, and interpreted before the page begins rendering (rendering begins when the browser receives the openning `<body>` tag). 



scripts marked as async are not guaranteed to execute in the order in which they are specified. Asynchronous scripts are guaranteed to execute before the page’s load event and may execute before or after DOMContentLoaded (see the “Events” chapter for details)



**Dynamic Script Loading**:

To inform preloaders of the existence of these dynamically requested files, you can explicitly declare them in the document head:

`<link rel="subresource" href="gibberish.js">`



**Changes in XHTML**:

1. There are two options for fixing the XHTML syntax error. The first is to replace all occurrences of the less-than symbol (<) with its HTML entity (<).
2. The second option for turning this code into a valid XHTML version is to wrap the JavaScript code in a CDATA section. In XHTML (and XML), CDATA sections are used to indicate areas of the document that contain free-form text not intended to be parsed.



**Inline code vs. External Files**:

- Maintainability:  It is much easier to have a directory for all JavaScript files so that developers can edit JavaScript code Independent of the markup in which it is used
- Caching: Browsers cache all externally linked JavaScript files according to specific settings, meaning that if two pages are using the same file, the file is downloaded only once. This ultimately means faster page-load times.
- Future-proof : By including JS using external files, there is no need to use XHTML or comment hacks mentioned previously. The syntax to include external files is the same for both HTMl and XHTML.



One notable consideration when configuring how external files are requested is their implication on request bandwidth. With SPDY/HTTP2, the per-request overhead is substantially reduced insofar as it may be advantageous to deliver scripts to the client as lightweight independent JavaScript components.

If the browser supports `SPDY/HTTP2`:

```html
<!-- First Page: -->
<script src="mainA.js"></script>
<script src="component1.js"></script>
<script src="component2.js"></script>
<script src="component3.js"></script>

<!-- Second Page: -->
<script src="mainB.js"></script>
<script src="component3.js"></script>
<script src="component4.js"></script>
<script src="component5.js"></script>
```

On the initial request, if the browser supports SPDY/HTTP2, it will be able to efficiently retrieve a number of files from the same endpoint, and it will enter them into the browser cache on a per-file basis. From the perspective of the browser, retrieval of these individual resources over SPDY/HTTP2 should have approximately the same latency as delivering a monolithic JavaScript payload.

One the second page request, because you segmented your application into lightweight cacheable files, some of the components that the second page also depends upon are already in the browser cache. 



**Document Modes**:

*quirk* mode:  Quirks mode is achieved in all browsers by omitting the doctype at the beginning of the document. This is considered poor practice because quirks mode is very different across all browsers, and no level of true browser consistency can be achieved without hacks.

*standard* mode: 

the primary difference between these two modes is related to the rendering of content with regard to CSS, there are also several side effects related to JavaScript.





**The nonscript Element**:

The `<noscript>` element can contain any HTML elements, aside from `<script> ` that can be included in the document `<body>` . Any content contained in a `<noscript>` element will be displayed under only the following two circumstances:

- The browser does not support scripting
- The browser's scripting support is turned off.







