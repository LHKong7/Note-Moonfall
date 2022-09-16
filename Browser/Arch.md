# 浏览器架构



SOA 体系架构



我们讲过 [进程与线程](https://fe.azhubaby.com/CSBasic/进程与线程.html) 的关系。进程就是应用程序创建的实例，而线程依托于进程。他们的关系：

- 进程中的任意一线程执行出错，会导致整个进程的奔溃
- 线程之间共享进程中的数据
- 当一个进程关闭之后，操作系统会回收进程所占用的内存
- 进程之间的内容相互隔离（很好地设计模型）



最终 Chrome 浏览器包括：1 个浏览器（Browser）主进程、1 个 GPU 进程、网络（NetWork）进程、多个渲染进程和多个插件进程

下面我们来逐个分析下这几个进程的功能。

- **浏览器进程**。主要负责界面显示、用户交互、子进程管理，同时提供存储等功能
- **渲染进程**。核心任务是将 HTML、CSS 和 JavaScript 转换为用户可以与之交互的网页，排版引擎 Blink 和 JavaScript 引擎 V8 都是运行在该进程中，默认情况下，Chrome 会为每个 Tab 标签创建一个渲染进程。出于安全考虑，渲染进程都是运行在沙箱模式下
- **GPU 进程**。其实，Chrome 刚开始发布的时候是没有 GPU 进程的。而 GPU 的使用初衷是实现 3D CSS 的效果，只是随后网页、Chrome 的 UI 界面都选择采用 GPU 来绘制，这使得 GPU 成为浏览器普遍的需求。最后，Chrome 在其多进程架构上也引入了 GPU 进程
- **网络进程**。主要负责页面的网络资源加载，之前是作为一个模块运行在浏览器进程里面的，直至最近才独立出来，成为一个单独的进程
- **插件进程**。主要是负责插件的运行，因插件易崩溃，所以需要通过插件进程来隔离，以保证插件进程崩溃不会对浏览器和页面造成影响



问题解决：

- 不稳定
- 不流程
- 不安全



##### 渲染进程中的线程

页面渲染，事件循环的基础。

**一句话解释**： 

- 渲染进程就是我们常说的浏览器内核，负责页面渲染，脚本执行，事件处理等，每个 tab 页就是一个渲染进程
- 渲染进程中包括 GUI 渲染线程、 JS 引擎线程、事件触发线程、网络异步线程、定时器线程
- 渲染进程内部包含主线程、工作线程、合成线程和光栅线程

渲染进程由以下线程组成：

- GUI渲染线程

  - 负责渲染浏览器界面，解析 HTML、CSS，构建 DOM 树和 RenderObject 树，布局和绘制等
  - 当界面需要重绘或由于某种操作引发回流时，该线程就会执行
  - 注意，GUI 渲染线程与 JS 引擎线程时互斥的，当 JS 引擎执行时 GUI 线程会被挂在，GUI 更新会被保存在一个队列中等待 JS 引擎空闲时立即被执行

- JS引擎线程

  - 也称为 JS 内核，负责处理 JavaScript 脚本程序（例如 V8 引擎）
  - 负责处理解析和执行 JavaScript 脚本程序
  - 只有一个 JS 引擎线程（单线程）
  - 与 GUI 渲染线程互斥，防止渲染结果不可预期

- 事件触发线程

  - 用来控制事件循环（鼠标点击、setTimeout、Ajax 等）
  - 当事件满足触发条件时，将事件放入到 JS 引擎所在的执行队列中
  - 归属于浏览器而不是`JS`引擎，用来控制事件循环

- 定时触发器线程

  - `setTimeout`和`setInterval`所在的线程
  - 定时任务并不是由 JS 引擎计时的，是由定时触发线程来计时
  - 计时完毕后，通知事件触发线程

- 异步HTTP请求线程

  - 浏览器有一个单独的线程用于处理 AJAX 请求
  - 当请求完成时，若有回调函数，通知事件触发线程

  

为什么GUI渲染线程与JS引擎线程互斥：

这是由于 JS 是可以操作 DOM 的，如果同时修改元素属性并同时渲染界面（即 JS 线程 和 UI 线程同时运行），那么渲染线程前后获得的元素就可能不一致了














