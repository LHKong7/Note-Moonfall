# Introduction to Node.js
    Nodejs is an open-source and cross-platform JavaScript runtime environment.
Node.js runs the V8 JavaScript engine, the core of Google Chrome, outside of the browser. This allows Node.js to be very performant.

A Node.js app runs in a single process, without creating a new thread for every request. 




##### Koa 洋葱模型

```js
const Koa = require('koa');

const app = new Koa();
const PORT = 3000;

// #1
app.use(async (ctx, next)=>{
    console.log(1)
    await next();
    console.log(1)
});
// #2
app.use(async (ctx, next) => {
    console.log(2)
    await next();
    console.log(2)
})

app.use(async (ctx, next) => {
    console.log(3)
})

app.listen(PORT);
console.log(`http://localhost:${PORT}`);

1
2
3
2
1
```

怎么样，是不是有一点点感觉了。当程序运行到`await next()`的时候就会暂停当前程序，进入下一个中间件，处理完之后才会仔回过头来继续处理。也就是说，当一个请求进入，`#1`会被第一个和最后一个经过，`#2`则是被第二和倒数第二个经过，依次类推。



koa的实现有几个最重要的点

1. context的保存和传递
2. 中间件的管理和next的实现

