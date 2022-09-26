# Same-origin policy



critical security mechanism that restricts how a document or script loaded by one origin can interact with a resource from another origin.



**Definition of origin**: Two URLs have the *same origin* if the ***protocol, port and host*** are the same for both. 



**Inherited origins**: 

**File origins**: Modern browsers usually treat the orgin of files loaded using the `file:///` schema as opaque origins. If a file includes other files from the same folder, they are not assumed to come from the same origin, and may trigger CORS errors



**Changing origin** (using the `documen.domain` is deprecated)



##### Cross-origin network access

The same-origin policy controls interactions between different origins, such as,`XMLHttpRequest` or `<img>` element

- Cross-origin writes are typically **allowed**. Examples: links, redirects and form submissions. Some HTTP requests require `preflight` -> ***the browser first sends an HTTP request using the [`OPTIONS`](https://developer.mozilla.org/en-US/docs/Web/HTTP/Methods/OPTIONS) method to the resource on the other origin, in order to determine if the actual request is safe to send. Such cross-origin requests are preflighted since they may have implications for user data.***
- Cross-origin embedding is typically allowed
  - JavaScript with `<script src="…"></script>`. Error details for syntax errors are only available for same-origin scripts.
  - CSS applied with `<link rel="stylesheet" href="…">`. Due to the [relaxed syntax rules](https://scarybeastsecurity.blogspot.com/2009/12/generic-cross-browser-cross-domain.html) of CSS, cross-origin CSS requires a correct `Content-Type` header. 
  - Images displayed by `<img>`
  - Media played by `<video` and `<audio>`
  - External resources embedded with `<object>` and `<embed>`
  - Fonts applied with [`@font-face`](https://developer.mozilla.org/en-US/docs/Web/CSS/@font-face). Some browsers allow cross-origin fonts, others require same-origin.
  - Anything embedded by`<iframe>` Sites can use the `X-Frame-Options`  header to prevent cross-origin framing.
- Cross-origin reads are typically disallowed, but read access is often leaked by embedding.





##### allow cross-origin access

Use [CORS](https://developer.mozilla.org/en-US/docs/Web/HTTP/CORS) to allow cross-origin access. CORS is a part of [HTTP](https://developer.mozilla.org/en-US/docs/Glossary/HTTP) that lets servers specify any other hosts from which a browser should permit loading of content.



##### block cross-origin access

- To prevent cross-origin writes: check an ungussable token in the request (known as a Cross-site request Forgery (CSRF)) token. You must prevent cross-origin reads of pages that require this token
- To prevent cross-origin reads of a resource, ensure that it is not embeddable. it is often necessary to prevent embedding because embedding a resources always leaks some information about it.
- To prevent cross-origin embeds, ensure that your resource cannot be interpreted as one of the embeddable formats listed above. Browsers may not respect the `Content-Type` header. For example, if you point a `<script>` tag at an HTML document, the browser will try to parse the HTML as JavaScript. When your resource is not an entry point to your site, you can also use a CSRF token to prevent embedding.



**Cross-origin script API access** 

JavaScript APIs like [`iframe.contentWindow`](https://developer.mozilla.org/en-US/docs/Web/API/HTMLIFrameElement/contentWindow), [`window.parent`](https://developer.mozilla.org/en-US/docs/Web/API/Window/parent), [`window.open`](https://developer.mozilla.org/en-US/docs/Web/API/Window/open), and [`window.opener`](https://developer.mozilla.org/en-US/docs/Web/API/Window/opener) allow documents to directly reference each other. When two documents do not have the same origin, these references provide very limited access to [`Window`](https://developer.mozilla.org/en-US/docs/Web/API/Window) and [`Location`](https://developer.mozilla.org/en-US/docs/Web/API/Location) objects, as described in the next two sections.

To communicate between documents from different origins, use [`window.postMessage`](https://developer.mozilla.org/en-US/docs/Web/API/Window/postMessage).



##### Cross-origin data storage access

Access to data stored in the browser such as [Web Storage](https://developer.mozilla.org/en-US/docs/Web/API/Web_Storage_API) and [IndexedDB](https://developer.mozilla.org/en-US/docs/Web/API/IndexedDB_API) are separated by origin. Each origin gets its own separate storage, and JavaScript in one origin cannot read from or write to the storage belonging to another origin.



**Cookies** use a separate definition of origins. A page can set a cookie for its own domain or any parent domain, as long as the parent domain is not a public suffix.

​	Firefox and Chrome use the [Public Suffix List](https://publicsuffix.org/) to determine if a domain is a public suffix.

The browser will make a cookie available to the given domain including any sub-domains, no matter which protocol (HTTP/HTTPS) or port is used. When you set a cookie, you can limit its availability using the `Domain`, `Path`, `Secure`, and `HttpOnly` flags. When you read a cookie, you cannot see from where it was set. Even if you use only secure https connections, any cookie you see may have been set using an insecure connection.

