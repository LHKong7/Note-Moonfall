

## What is Node.js

Node (Node.js) is an ***event-driven I/O framework*** for V8 JavaScript engine. Nodejs allows JS to be executed on the server side, and it uses V8 engine.



##### Basic Philosophy of Nodejs:

- **Non-blocking I/O** - every I/O call must take a callback, whether it is to retrieve information from disk, network or another process.
- **Built-in support for the most important protocols** (HTTP, DNS, TLS)
- **Low-level**. Do not remove functionality present at the POSIX layer. For example, support half-closed TCP connections.
- **Stream everything**; never force the buffering of data.



**Event Loop**: a mechanism which allows you to specify what happens when a particular event occur.  

​		CPU-intensive task that takes four seconds to complete, then a Node server would not be able to respond to other requests during those four seconds, since the event loop is only checked for new tasks once your code finishes.



The premise of Node is that I/O is the main bottleneck of many tasks. A single I/O operation can take millions of CPU cycles, and in traditional, non-event-loop based frameworks the execution is blocked for that time. In Node, I/O operations such as reading a file are performed asynchronously.



an event loop is “an entity that handles and processes external events and converts them into callback invocations”.



When code is running, the Node runtime starts up, loads the V8 JavaScript engine which runs the scrips.



### Control Flow



