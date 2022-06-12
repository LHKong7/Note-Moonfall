# What is JavaScript



### ECMAScript



Web Browser are just one host environment where an ECMAScript implementation may exist. A host environment provides the base implementation of ECMAScript and implementation extensions designed to interface with the environment itself. Extensions such as the DOM and BOM.

Nodejs: a host environment of JavaScript for server-side.

ES6 means the edition of ECMAScript 6

**The Document Model**:  The Document Object Model (DOM) is an application programming interface (API) for XML that was extended for use in HTML. The DOM maps out an entire page as a hierarchy of nodes. Each part of an HTML or XML page is a type of node containing different kinds of data.

**DOM Levels:**

DOM Level 1: two modules →

- DOM Core: provide a way to map the structure of an XML-based document to allow for easy access and manipulation of any part of a document
- DOM HTML: extended the DOM Core by adding HTML-specifc objects and methods

DOM Level 2:  introduces the following new modules of the DOM to deal with new types of interfaces:

- DOM views → describes interfaces to keep track of the various views of a document (the document before and after CSS styling)
- DOM events → describes interfaces for events and event handling
- DOM style → describes interfaces to deal with CSS-based styling of elements
- DOM traversal and range → describes interfaces to traverse and manipulate a document tree

DOM Level 3: extends the DOM with the introduction of methods to load and save document in a uniform way (contained in a new module called DOM Load and Save) and methods to validate a document (DOM Validation). In level 3, the DOM Core is extended to support all of XML 1.0, including XML Infoset, XPath and XML base.

Scalable Vector Graphics (SVG) 1.0

Mathematical Markup Language (Math ML) 1.0

Synchronized Multimedia Integration Language (SMIL)

### The Browser Object Model

allowed access and manipulation of the browser window. Using the BOM, developers can interact with the browser outside of the context of its displayed page.

The BOM deals with the browser window and frames, but generally any browser specific extension to JavaScript is considered to be a part of the BOM.

- The capbility to pop up new browser window
- The capability to move, resize, and close browser windows
- The `navigator` object, which provides detailed information about the browser
- The `location` object which gives detailed information baout the page loaded in the browser.
- The `screen` object, which gives detailed information about the user’s screen resolution
- The `performance` object, which gives detailed information about the browser’s memory consumption, navigational behavior, and timing statistics
- Support for cookies
- Custom objects such as `XMLHttpRequest` and Internet Explorer’s `ActiveXObject`
