

[TOC]



https://juejin.cn/post/6850418118854967304#heading-2

# JavaScript Knowledge Prepartion

### JS knowledge

##### var let & const

在现代js中，let＆const是创建变量的不同方式。 在早期的js中，咱们使用var关键字来创建变量。 let＆const关键字是在ES6版本中引入的，其目的是在js中创建两种不同类型的变量，一种是不可变的，另一种是可变的。

**const**:它用于创建一个不可变变量。不可变变量是指其值在程序的整个生命周期中永不改变的变量。

**let**: let用于创建一个可变变量，可变变量是像var这样的普通变量，可以任意次数地更改。



##### JS 中的主要有哪几类错误

JS有三类的错误:

**加载时错误**：加载web页面时出现的错误(如语法错误)称为加载时错误，它会动态生成错误。

**运行时错误**：由于滥用html语言中的命令而导致的错误。

**逻辑错误**：这些错误是由于对具有不同操作的函数执行了错误的逻辑而导致的



##### 如何通过类别名获取 dom 元素

在 JS 中使用document.getElementsByClassName() 方法来获取具有类名的元素。

##### JS的作用域链是什么及其作用

一般情况下，变量取值到创建这个变量的函数的作用域中取值。但是如果在当前作用域中没有查到值，就会向上级作用域去查，直到查到**全局作用域**，这么一个查找过程形成的链条就叫做**作用域链**。

JS中的作用域链主要用于解析变量的值。 如果没有这个，在不同的作用域内定义了许多变量，JS很难为变量选择某个值。

##### 解释JS中的MUL函数

MUL表示数的简单乘法。在这种技术中，将一个值作为参数传递给一个函数，而该函数将返回另一个函数，将第二个值传递给该函数，然后重复继续。例如:x*y*z可以表示为

```js
function mul (x) {  
 return function (y) { 
   return function (z) {   
     return x * y * z;
   }
  }
}
```

##### 用纯JS编写一个程序来反转字符串

```js
str="jQuery";
str = str.split("")
str = str.reverse()
str = str.join("")
alert(str);
```

首先将字符串拆分为数组，然后反转数组，最近将字符连接起来形成字符串。

**使用循环**:首先，计算字符串中的字符数，然后对原始字符串应用递减循环，该循环从最后一个字符开始，打印每个字符，直到count变为零。



##### JS中如何将页面重定向到另一个页面？

```
使用 location.href：window.location.href =“https://www.onlineinterviewquestions.com/”

使用 location.replace： window.location.replace(" https://www.onlineinterviewquestions.com/;");
```



##### 列出JS中的一些设计模式:

设计模式是软件设计中常见问题的通用可重用解决方案，以下是一些设计模式是：

**创建模式**：该模式抽象了对象实例化过程。

**结构型模式**：这些模式处理不同的类和对象以提供新功能。

**行为模式**：也称**发布-订阅模式**，定义了一个被观察者和多个观察者的、一对多的对象关系。

**并行设计模式**：这些模式处理多线程编程范例。

**架构设计模式**：这些模式用于处理架构设计。



##### JS中的Array.splice()和Array.slice()方法有什么区别

```js
var arr=[0,1,2,3,4,5,6,7,8,9];//设置一个数组
console.log(arr.slice(2,7));//2,3,4,5,6
console.log(arr.splice(2,7));//2,3,4,5,6,7,8
//由此我们简单推测数量两个函数参数的意义,
slice(start,end)第一个参数表示开始位置,第二个表示截取到的位置(不包含该位置)
splice(start,length)第一个参数开始位置,第二个参数截取长度
```

##### 如何在JS中动态添加/删除对象的属性？

咱们可以使用object.property_name = value向对象添加属性，delete object.property_name 用于删除属性。

```js
let user = new Object();
// adding a property
user.name='Anil';
user.age  =25;
console.log(user);
delete user.age;
console.log(user);
```



##### 解释一下什么是 promise ？

promise是js中的一个对象，用于生成可能在将来产生结果的值。 值可以是已解析的值，也可以是说明为什么未解析该值的原因。

promise 可以有三种状态:

pending：初始状态，既不是成功也不是失败

fulfilled：意味着操作完全成功

rejected：意味着操作失败

一个等待状态的promise对象能够成功后返回一个值，也能失败后带回一个错误
当这两种情况发生的时候，处理函数会排队执行通过then方法会被调用。



##### 数组去重复的方法有哪些

```
function uniquearray(array) { 
 let unique_array= Array.from(set(array)) 
 return unique_array;
}


function unque_array (arr) {
  let unique_array = arr.filter(function(elem, index, self) {
    return index == self.indexOf(elem);
  })
  return unique_array;
}

 console.log(unique_array(array_with_duplicates));
 
 
 Array dups_names = ['Ron', 'Pal', 'Fred', 'Rongo', 'Ron'];
function dups_array(dups_names) {
 let unique = {};
 names.forEach(function(i) {
    If (!unique[i]) {
      unique[i] = true;    }
  });
return Object.keys(unique);}   // Ron, Pal, Fred, Rongo
Dups_array(names);
```



##### undefined，null 和 undeclared 有什么区别？

1.null表示"没有对象"，即该处不应该有值，转为数值时为0。典型用法是：

（1） 作为函数的参数，表示该函数的参数不是对象。

（2） 作为对象原型链的终点。

2.undefined表示"缺少值"，就是此处应该有一个值，但是还没有定义，转为数值时为NaN。典型用法是：

（1）变量被声明了，但没有赋值时，就等于undefined。

（2) 调用函数时，应该提供的参数没有提供，该参数等于undefined。

（3）对象没有赋值的属性，该属性的值为undefined。

（4）函数没有返回值时，默认返回undefined。

3.undeclared：js语法错误，没有申明直接使用，js无法找到对应的上下文。



##### 列出JS基本和非基本数据类型之间的一些区别？

1.目前JS中有6种基本数据类型: Undefined、Null、Boolean、Number、Symbol 和 String。还有1种复杂的数据类型————Object，Object本质上是由一组无序的名值对组成的。Object、Array和Function则属于引用类型。

2.基本数据类型是不可变的，而非基本数据类型是可变的。

3.基本数据类型是不可变的，因为它们一旦创建就无法更改，但非基本数据类型刚可更改，意味着一旦创建了对象，就可以更改它。

4.将基本数据类型与其值进行比较，这意味着如果两个值具有相同的数据类型并具有相同的值，那么它们是严格相等的。

5.非基本数据类型不与值进行比较。例如，如果两个对象具有相同的属性和值，则它们严格不相等。



#####  如何在现有函数中添加新属性

只需给现有函数赋值，就可以很容易地在现有函数中添加新属性。例如，现有一个对象person，通过下面的代码来为 person 添加新的属性：

```js
person.country= “India”;
```



#### 16. JS中的深拷贝与浅拷贝的区别？

深拷贝递归地复制新对象中的所有值或属性，而拷贝只复制引用。

在深拷贝中，新对象中的更改不会影响原始对象，而在浅拷贝中，新对象中的更改，原始对象中也会跟着改。

在深拷贝中，原始对象不与新对象共享相同的属性，而在浅拷贝中，它们具有相同的属性。

#### 17. 如何在JavaScript中每x秒调用一个函数

在JS中，咱们使用函数 setInterval() 在每x秒内调用函数。如：

```
setInterval(function (){ alert("Hello"); }, 3000);
```

#### 18. 解释一下JS的展开操作符？

展开运算符在需要多个参数/变量/元素的位置展开表达式，它用三个点（...）。如：

```
var mid = [3, 4];

var newarray = [1, 2, ...mid, 5, 6];

console.log(newarray);

// [1, 2, 3, 4, 5, 6]
```

#### 19. JS中的宿主对象与原生对象有何不同？

**宿主对象**:这些是运行环境提供的对象。这意味着它们在不同的环境下是不同的。例如，浏览器包含像windows这样的对象，但是**Node.js**环境提供像Node List这样的对象。

**原生对象**:这些是JS中的内置对象。它们也被称为全局对象，因为如果使用JS，内置对象不受是运行环境影响。

#### 20. 解释JS中的高阶函数？

高阶函数是JS函数式编程的最佳特性。它是以函数为参数并返回函数作为结果的函数。一些内置的高阶函数是map、filter、reduce 等等。

#### 21. JS 中 == 和 === 区别是什么？

1、对于string,number等基础类型，==和===有区别

1）不同类型间比较，==之比较“转化成同一类型后的值”看“值”是否相等，===如果类型不同，其结果就是不等。
2）同类型比较，直接进行“值”比较，两者结果一样。

2、对于Array,Object等高级类型，==和===没有区别

进行“指针地址”比较。

3、基础类型与高级类型，==和===有区别

1）对于==，将高级转化为基础类型，进行“值”比较。
2）因为类型不同，===结果为false。

#### 22. JS中的匿名函数是什么？

匿名函数：就是没有函数名的函数，如：

```
(function(x, y){
    alert(x + y);  
})(2, 3);
```

这里创建了一个匿名函数(在第一个括号内)，第二个括号用于调用该匿名函数，并传入参数。

#### 23. 是否可以在JS中执行301重定向？

JS完全运行在客户端上。301是服务器作为响应发送的响应代码。因此，在JS中不可能执行301重定向。

#### 24. 解释JS中的事件冒泡和事件捕获

**事件捕获和冒泡**: 在html DOM API中，有两种事件传播方法，它们决定了接收事件的顺序。两种方法是事件冒泡和事件捕获。第一个方法事件冒泡将事件指向其预期的目标，第二个方法称为事件捕获，其中事件向下到达元素。

**事件捕获**

捕获过程很少被使用，但是当它被使用时，它被证明是非常有用的。这个过程也称为滴流模式。在这个过程中，事件首先由最外层的元素捕获，然后传播到最内部的元素。例如:

```
<div>
  <ul>
    <li></li>
  </ul>
</div>
```

从上面的示例中，假设单击事件发生在li元素中，在这种情况下，捕获事件将首先处理div，然后处理ul，最后命中目标元素li。

**事件冒泡**

冒泡的工作原理与冒泡类似，事件由最内部的元素处理，然后传播到外部元素。

```
<div>
  <ul>
    <li></li>
  </ul>
</div>
```

从上面的例子中，假设click事件确实发生在冒泡模型中的li元素中，该事件将首先由li处理，然后由ul处理，最后由div元素处理。

#### 24. 如何将文件的所有导出作为一个对象？

import * as objectname from ‘./file.js’用于将所有导出的成员导入为对象。 可以使用对象的点（.）运算符来访问导出的变量或方法，如：

```
objectname.member1;
objectname.member2;
objectname.memberfunc();
```

#### 25. 解释一下什么是箭头函数？

箭头函数是在es6或更高版本中编写函数表达式的简明方法。箭头函数不能用作构造函数，也不支持this，arguments，super或new.target关键字，它最适合非方法函数。 通常，箭头函数看起来像 const function_name =（）=> {}。

```
const greet=()=>{console.log('hello');}
 greet();
```

#### 25 解释 JS 中的函数提升

JS允许将声明移动到顶部的默认行为称为**提升**。JS中创建函数的两种方法是函数声明和函数表达式。

**函数声明**

具有特定参数的函数称为函数声明，在JS中创建变量称为声明。如：

```
hoisted(); // logs "foo"

function hoisted() {
  console.log('foo');
}
```

**函数表达式**

当使用表达式创建函数时，称为函数表达式。如：

```
notHoisted(); // TypeError: notHoisted is not a function

var notHoisted = function() {
   console.log('bar');
};
```

#### 26. module.exports 和 exports 之间有什么区别？

module和exports是Node.js给每个js文件内置的两个对象。可以通过console.log(module)和console.log(exports)打印出来。如果你在main.js中写入下面两行，然后运行$ node main.js:

```
console.log(exports);//输出：{}
console.log(module);//输出：Module {..., exports: {}, ...} （注：...代表省略了其他一些属性）
```

从打印咱们可以看出，module.exports和exports一开始都是一个空对象{}，实际上，这两个对象指向同一块内存。这也就是说module.exports和exports是等价的（有个前提：不去改变它们指向的内存地址）。

例如：exports.age = 18和module.export.age = 18，这两种写法是一致的（都相当于给最初的空对象{}添加了一个属性，通过require得到的就是{age: 18}）。

#### 27. import 和 exports 是什么？

import和exports 帮助咱们编写模块化的JS代码。使用import和exports，咱们可以将代码分割成多个文件。import只允许获取文件的某些特定变量或方法。可以导入模块导出的方法或变量。

```
 //index.js

 import name,age from './person'; 

 console.log(name);
 console.log(age);

 //person.js

 let name ='Sharad', occupation='developer', age =26;

 export { name, age}; 
```

#### 28. 列出一些单元测试框架

下面是一些最流行的JS单元测试框架:

Unit.js

Jasmine

Karma

Chai

AVA

Mocha

JSUnit

QUnit

Jest

#### 29. JS中有哪些不同类型的弹出框可用

在JS中有三种类型的弹出框可用，分别是：

Alert

Confirm

Prompt

#### 30. 如何将 JS 日期转换为ISO标准

**toISOString()** 方法用于将js日期转换为ISO标准。 它使用ISO标准将js Date对象转换为字符串。如：

```
var date = new Date();
var n = date.toISOString();
console.log(n);
// YYYY-MM-DDTHH:mm:ss.sssZ
```

#### 31. 如何在JS中克隆对象

Object.assign() 方法用于在JS中克隆对象。如：

```
var x = {myProp: "value"};
var y = Object.assign({}, x); 
```

#### 32. 如何在JS中编码和解码 URL

**encodeURI()** 函数用于在JS中对URL进行编码。它将url字符串作为参数并返回编码的字符串。

**注意**： encodeURI()不会编码类似这样字符： / ? : @ & = + $ #，如果需要编码这些字符，请使用encodeURIComponent()。 用法：

```
var uri = "my profile.php?name=sammer&occupation=pāntiNG";
var encoded_uri = encodeURI(uri);
```

**decodeURI()** 函数用于解码js中的URL。它将编码的url字符串作为参数并返回已解码的字符串，用法：

```
var uri = "my profile.php?name=sammer&occupation=pāntiNG";
var encoded_uri = encodeURI(uri);
decodeURI(encoded_uri);
```

#### 33. BOM 和 DOM 的关系

**BOM**全称Browser Object Model，即浏览器对象模型，主要处理浏览器窗口和框架。

DOM全称Document Object Model，即文档对象模型，是 HTML 和XML 的应用程序接口（API），遵循W3C 的标准，所有浏览器公共遵守的标准。

JS是通过访问**BOM**（Browser Object Model）对象来访问、控制、修改客户端(浏览器)，由于**BOM**的window包含了document，window对象的属性和方法是直接可以使用而且被感知的，因此可以直接使用window对象的document属性，通过document属性就可以访问、检索、修改XHTML文档内容与结构。因为document对象又是DOM的根节点。

可以说，BOM包含了DOM(对象)，浏览器提供出来给予访问的是BOM对象，从BOM对象再访问到DOM对象，从而js可以操作浏览器以及浏览器读取到的文档。

#### 34. JS中的substr()和substring()函数有什么区别

substr() 函数的形式为substr(startIndex,length)。 它从startIndex返回子字符串并返回'length'个字符数。

```
var s = "hello";
( s.substr(1,4) == "ello" ) // true
```

substring() 函数的形式为substring(startIndex,endIndex)。 它返回从startIndex到endIndex - 1的子字符串。

```
var s = "hello";
( s.substring(1,4) == "ell" ) // true
```

#### 35. 解释一下 "use strict" ?

“use strict”是Es5中引入的js指令。 使用“use strict”指令的目的是强制执行严格模式下的代码。 在严格模式下，咱们不能在不声明变量的情况下使用变量。 早期版本的js忽略了“use strict”。

#### 36.解释 JS 事件委托模型？

在JS中，有一些很酷的东西。其中之一是委托模型。当捕获和冒泡时，允许函数在一个特定的时间实现一个处理程序到多个元素，这称为事件委托。事件委托允许将事件侦听器添加到父节点而不是指定的节点。这个特定的侦听器分析冒泡事件，以找到子元素上的匹配项。



##### JavaScript规定了几种数据类型

js目前共定义了8种数据类型，其中包括：Undefined,Null,Boolean，Number，String，Object， Symbol,BigInt



##### JavaScript对象的底层数据结构是什么

JavaScript基本类型数据都是直接按值存储在栈中的(Undefined、Null、不是new出来的布尔、数字和字符串)，每种类型的数据占用的内存空间的大小是确定的，并由系统自动分配和自动释放。这样带来的好处就是，内存可以及时得到回收，相对于堆来说 ，更加容易管理内存空间。

JavaScript引用类型数据被存储于堆中 (如对象、数组、函数等，它们是通过拷贝和new出来的）。其实，说存储于堆中，也不太准确，因为，引用类型的数据的地址指针是存储于栈中的，当我们想要访问引用类型的值的时候，需要先从栈中获得对象的地址指针，然后，在通过地址指针找到堆中的所需要的数据。



##### Symbol类型在实际开发中的应用、可手动实现一个简单的Symbol

1. 使用Symbol来替代常量

   ```js
   const TYPE_AUDIO = Symbol()
   const TYPE_VIDEO = Symbol()
   const TYPE_IMAGE = Symbol()
   ```

   

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

   由于Symbol常量PASSWORD被定义在a.js所在的模块中，外面的模块获取不到这个Symbol，也不可能再创建一个一模一样的Symbol出来（因为Symbol是唯一的），因此这个PASSWORD的Symbol只能被限制在a.js内部使用，所以使用它来定义的类属性是没有办法被模块外访问到的，达到了一个私有化的效果

   

4. 注册和获取全局Symbol window中创建的Symbol实例总是唯一的，而我们需要的是在所有这些window环境下保持一个共享的Symbol。这种情况下，我们就需要使用另一个API来创建或获取Symbol，那就是Symbol.for()，它可以注册或获取一个window间全局的Symbol实例：


   ```js
   let gs1 = Symbol.for('global_symbol_1')  //注册一个全局Symbol
   let gs2 = Symbol.for('global_symbol_1')  //获取全局Symbol
   gs1 === gs2  // true
   ```

##### JavaScript中的变量在内存中的具体存储形式

基本类型是保存在栈内存中的简单数据段，它们的值都有固定的大小，保存在栈空间，通过按值访问

引用类型是保存在堆内存中的对象，值大小不固定，栈内存中存放的该对象的访问地址指向堆内存中的对象，JavaScript不允许直接访问堆内存中的位置，因此操作对象时，实际操作对象的引用

```js
let a1 = 0; // 栈内存
let a2 = "this is string" // 栈内存
let a3 = null; // 栈内存
let b = { x: 10 }; // 变量b存在于栈中，{ x: 10 }作为对象存在于堆中
let c = [1, 2, 3]; // 变量c存在于栈中，[1, 2, 3]作为对象存在于堆中
```

##### 基本类型对应的内置对象，以及他们之间的装箱拆箱操作

**内置对象：** Object是 JavaScript 中所有对象的父对象 数据封装类对象：Object、Array、Boolean、Number 和 String 其他对象：Function、Math、Date、RegExp、Error。 特殊的基本包装类型(String、Number、Boolean) arguments: 只存在于函数内部的一个类数组对象 **装箱：** 把基本数据类型转化为对应的引用数据类型的操作，装箱分为隐式装箱和显示装箱 **隐式装箱**


```js
let a = 'sun'
let b = a.indexof('s') // 0 // 返回下标

// 上面代码在后台实际的步骤为
let a = new String('sun')
let b = a.indexof('s')
a = null
```

**实现机制：**

1.创建String类型的一个实例； 2.在实例上调用指定的方法； 3.销毁这个实例；

**显示装箱** 通过内置对象可以对Boolean、Object、String等可以对基本类型显示装箱 let a = new String('sun')

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

##### 理解值类型和引用类型

|          | 值类型                                                       | 引用类型                               |
| -------- | ------------------------------------------------------------ | -------------------------------------- |
| 存储方式 | 直接存储数据本身                                             | 存储的是数据的引用，数据存储在数据堆中 |
| 内存分配 | 分配在栈中                                                   | 分配在堆中                             |
| 效率     | 效率高，不需要地址转换                                       | 效率较低，需要进行地址转换             |
| 内存回收 | 使用完后立即回收                                             | 使用完后不立即回收，而是交给GC处理回收 |
| 赋值操作 | 创建一个新对象                                               | 创建一个引用                           |
| 类型拓展 | 不易拓展，所有值都是密封的（seal），所以无法派生出新的值类型 | 具有多态的特性方便拓展                 |
| 实例分配 | 通常是在线程栈上分配的（静态分配）但是在某些情形下可以存储在堆中 | 总是在进程堆中分配（动态分配）         |



##### null和undefined的区别

##### null表示"没有对象"，即该处不应该有值。典型用法是:

（1） 作为函数的参数，表示该函数的参数不是对象。
 （2） 作为对象原型链的终点。

##### undefined表示"缺少值"，就是此处应该有一个值，但是还没有定义。典型用法是：

（1）变量被声明了，但没有赋值时，就等于undefined。
 （2) 调用函数时，应该提供的参数没有提供，该参数等于undefined。
 （3）对象没有赋值的属性，该属性的值为undefined。
 （4）函数没有返回值时，默认返回undefined。


##### 至少可以说出三种判断JavaScript数据类型的方式，以及他们的优缺点，如何准确的判断数组类型

1、typeof:（可以对基本类型做出准确的判断，但对于引用类型，用它就有点力不从心了）

typeof 返回一个表示数据类型的字符串，返回结果包括：number、boolean、string、object、undefined、function等6种数据类型。

2、instanceof

instanceof是用来判断A是否为B的实例时，表达式为：A instanceof B,如果 A是B的实例，则返回true; 否则返回false 在这里特别注意的是 instanceof检测的是原型

3 Object.prototype.toString

toString是Object原型对象上的一个方法，该方法默认返回其调用者的具体类型，更严格的讲，是 toString运行时this指向的对象类型, 返回的类型格式为[object,xxx],xxx是具体的数据类型，其中包括：String,Number,Boolean,Undefined,Null,Function,Date,Array,RegExp,Error,HTMLDocument,… 基本上所有对象的类型都可以通过这个方法获取到。

 **4 constructor 查看对象对应的构造函数** construvtor在对应对象的原型下面，是自动生成的，当我们写一个构造函数的时候，程序自动添加，构造函数名.prototype.constructor = 构造函数名



##### 可能发生隐式类型转换的场景以及转换原则，应如何避免或巧妙应用



##### 出现小数精度丢失的原因，JavaScript可以存储的最大数字、最大安全数字，JavaScript处理大数字的方法、避免精度丢失的方法

0.1+0.2不等于0.3，是因为计算机进行计算时先转化成二进制，二浮点数用二进制表示时是无穷位的，IEEE754标准中用64位表示（1位用来表示符号位，11用来表示指数，52位表示尾数）会截断后面的位数，再转化成十进制，就有了误差。

**最大数字：**

对于整数，前端出现问题的几率可能比较低，毕竟很少有业务需要需要用到超大整数，只要运算结果不超过 Math.pow(2, 53) 就不会丢失精度。

对于小数，前端出现问题的几率还是很多的，尤其在一些电商网站涉及到金额等数据。解决方式：把小数放到位整数（乘倍数），再缩小回原来倍数（除倍数）

最安全的数字-Math.pow(2, 53)-1,到+Math.pow(2, 53)-1



#### 原型和原型链

###### instanceof的底层实现原理，手动实现一个instanceof

```js
function new_instance_of(leftVaule, rightVaule) { 
    let rightProto = rightVaule.prototype; // 取右表达式的 prototype 值
    leftVaule = leftVaule.__proto__; // 取左表达式的__proto__值
    while (true) {
    	if (leftVaule === null) {
            return false;	
        }
        if (leftVaule === rightProto) {
            return true;	
        } 
        leftVaule = leftVaule.__proto__ 
    }
}
```

##### 实现继承的几种方式以及他们的优缺点

##### 可以描述new一个对象的详细过程，手动实现一个new操作符

```js
function Person (name,age){
    this.name = name;
    this.age = age;
    this.say = function () {
        console.log("I am " + this.name)
    }
}
function realizeNew(){
    let obj = {};
    let Con = [].shift.call(arguments);
    obj.__proto__ = Con.prototype;
    let result = Con.apply(obj,arguments);
    return typeof result === 'object'? result : obj
}
var person1 =realizeNew(Person,'张三')
```

#### 作用域和闭包

##### 理解词法作用域和动态作用域

**词法作用域**，函数的作用域在函数定义的时候就决定了（取决于函数定义的位置）
**动态作用域**，函数的作用域在函数调用的时候就决定了（取决于函数的调用） js采用的是词法作用域



##### 理解JavaScript的作用域和作用域链

作用域就是一个独立的地盘，让变量不会外泄、暴露出去。也就是说作用域最大的用处就是隔离变量，不同作用域下同名变量不会有冲突。 ES6 之前 JavaScript 没有块级作用域,只有全局作用域和函数作用域。ES6的到来，为我们提供了‘块级作用域’,可通过新增命令let和const来体现。

```js
function outFun2() {
    var inVariable = "内层变量2";
}
outFun2();//要先执行这个函数，否则根本不知道里面是啥
console.log(inVariable); // Uncaught ReferenceError: inVariable is not defined
```

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



##### this的原理以及几种不同使用场景的取值

this 既不指向函数自身，也不指函数的词法作用域，而是调用函数时的对象！

1. **普通函数的调用，this指向的是Window**

   ```
   var name = '卡卡';
   function cat(){
       var name = '有鱼';
       console.log(this.name);//卡卡
       console.log(this);//Window {frames: Window, postMessage: ƒ, blur: ƒ, focus: ƒ, close: ƒ, …}
   }
   cat();
   ```

   

2. **对象的方法，this指的是该对象**

   1. 一层作用域链时，this指的该对象

      ```
      var name = '卡卡';
      var cat = {
          name:'有鱼',
          eat:function(){
              console.log(this.name);//有鱼
          }
      }
      cat.eat();
      ```

      

   2. 多层作用域链时，this指的是距离方法最近的一层对象

      ```js
      var name = '卡卡';
      var cat = {
          name:'有鱼',
          eat1:{
              name:'年年',
              eat2:function(){
                  console.log(this.name);//年年
              }
          }
      }
      cat.eat1.eat2();
      
      var eat3 = cat.eat1.eat2;
      eat3(); // 卡卡
      ```

      

3. **构造函数的调用，this指的是实例化的新对象**

   ```js
   var name = '卡卡';
   function Cat(){
       this.name = '有鱼';
       this.type = '英短蓝猫';
   }
   var cat1 = new Cat();
   console.log(cat1);// 实例化新对象 Cat {name: "有鱼", type: "英短蓝猫"}
   console.log(cat1.name);// 有鱼
   ```

   

4. **apply和call调用时，this指向参数中的对象**

   ```js
   var name = '有鱼';
   function eat(){
       console.log(this.name);
   }
   var cat = {
       name:'年年',
   }
   var dog = {
       name:'高飞',
   }
   
   eat.call(cat);// 年年
   eat.call(dog);// 高飞
   ```

   

5. **匿名函数调用，指向的是全局对象**

   ```js
   var name = '卡卡';
   var cat = {
       name:'有鱼',
       eat:(function(){
           console.log(this.name);//卡卡
       })()
   }
   cat.eat;
   ```

   

6. **定时器中调用，指向的是全局变量**

```js
var name = '卡卡';
var cat = setInterval(function(){
    var name = '有鱼';
    console.log(this.name);// 卡卡
    clearInterval(cat);
},500);
```

①普通函数的调用，this指向的是window
 ②对象方法的调用，this指的是该对象，且是最近的对象
 ③构造函数的调用，this指的是实例化的新对象
 ④apply和call调用，this指向参数中的对象
 ⑤匿名函数的调用，this指向的是全局对象window
 ⑥定时器中的调用，this指向的是全局变量window

##### 闭包的实现原理和作用，可以列举几个开发中闭包的实际应用

闭包就是能够读取其他函数内部变量的函数 它的最大用处有两个，一个是前面提到的可以读取函数内部的变量，另一个就是让这些变量的值始终保持在内存中。

```js
function f1() {
    var n = 999;
    nAdd = function () {
        n += 1
    }

    function f2() {
        alert(n);
    }
    return f2;
}
var result = f1();
result(); // 999
nAdd();
result(); // 1000
```

在这段代码中，result实际上就是闭包f2函数。它一共运行了两次，第一次的值是999，第二次的值是1000。这证明了，函数f1中的局部变量n一直保存在内存中，并没有在f1调用后被自动清除。 为什么会这样呢？

原因就在于f1是f2的父函数，而f2被赋给了一个全局变量，这导致f2始终在内存中，而f2的存在依赖于f1，因此f1也始终在内存中，不会在调用结束后，被垃圾回收机制（garbage collection）回收。 这段代码中另一个值得注意的地方，就是"nAdd=function(){n+=1}"这一行，首先在nAdd前面没有使用var关键字，因此nAdd是一个全局变量，而不是局部变量。其次，nAdd的值是一个匿名函数（anonymous function），而这个匿名函数本身也是一个闭包，所以nAdd相当于是一个setter，可以在函数外部对函数内部的局部变量进行操作



##### 理解堆栈溢出和内存泄漏的原理，如何防止

**1、内存泄露**：是指申请的内存执行完后没有及时的清理或者销毁，占用空闲内存，内存泄露过多的话，就会导致后面的程序申请不到内存。因此内存泄露会导致内部内存溢出 

**2、堆栈溢出**：是指内存空间已经被申请完，没有足够的内存提供了

常见的手段是将一个变量置为null，该变量就会被下一轮垃圾回收机制回收。 常见的内存泄露的原因：

- 全局变量引起的内存泄露
- 闭包
- 没有被清除的计时器

解决方法：

- 减少不必要的全局变量
- 严格使用闭包（因为闭包会导致内存泄露）
- 避免死循环的发生





##### Closure

Closures are **frequently used in JavaScript** for object data privacy, in event handlers and callback functions, and in [partial applications, currying](https://medium.com/javascript-scene/curry-or-partial-application-8150044c78b8#.l4b6l1i3x), and other functional programming patterns.

A **closure** is the combination of a function bundled together (enclosed) with references to its surrounding state (the **lexical environment**). In other words, a closure gives you access to an outer function’s scope from an inner function. In JavaScript, closures are created every time a function is created, at function creation time.

​	To use a closure, define a function inside another function and expose it. To expose a function, return it or pass it to another function.

​	The inner function will have access to the variables in the outer function scope, even after the outer function has returned.

Among other things, closures are commonly used to give objects data privacy. Data privacy is an essential property that helps us program to an interface, not an implementation. 

1. In JavaScript, closures are the primary mechanism used to enable data privacy. When you use closures for data privacy, the enclosed variables are only in scope within the containing (outer) function. You can’t get at the data from an outside scope except through the object’s **privileged methods**. In JavaScript, any exposed method defined within the closure scope is privileged. 

2. Objects are not the only way to produce data privacy. Closures can also be used to create **stateful functions** whose return values may be influenced by their internal state

In functional programming, closures are frequently used for partial application & currying.

```js
// Generic Partial Application Function
// https://jsbin.com/biyupu/edit?html,js,output
// https://gist.github.com/ericelliott/f0a8fd662111ea2f569e

// partialApply(targetFunction: Function, ...fixedArgs: Any[]) =>
//   functionWithFewerParams(...remainingArgs: Any[])
const partialApply = (fn, ...fixedArgs) => {
  return function (...remainingArgs) {
    return fn.apply(this, fixedArgs.concat(remainingArgs));
  };
};


test('add10', assert => {
  const msg = 'partialApply() should partially apply functions'

  const add = (a, b) => a + b;

  const add10 = partialApply(add, 10);


  const actual = add10(5);
  const expected = 15;

  assert.equal(actual, expected, msg);
});
```

##### TODO: Object Pool Design





##### async/await

1. `aysnc` 返回的也是一个 `Promise` 对象。
2. 如果返回了`return 标量` 或 `throw Error` 则返回 `{PromiseStatus: resolved/rejected}` 的 `Promise`对象。
3. 如果遇到了`await`装饰的`Promise`，则返回 `{PromiseStatus: pending}` 的 `Promise`。并等待此`Promise`的执行结果：如果`Promise`触发了`resolve`则获取结果并继续向下执行；如果`Promise`触发了`reject`则抛出一个异常。所以我们在使用时应将代码使用`try...catch`封装。
4. `await` 关键字只能在 `async`内使用，`await`主要意图是装饰一个以 `{PromiseStatus: pending}`的状态返回的`Promise`对象（任何 JS 表达式都可以，但没什么意义），并等待其后续的`resolved/rejected`状态更新，从而决定是获得结果并继续向下执行，还是终止并抛出异常。

```js
var url = window.location.href

async function getUrls(url1, url2, url3) {
    try {
        // req1 success or throw error (promise reject)
        let res1 = await asyncHttpGet(url1);
        
        // req2 success or throw error (promise reject)
        let res2 = await asyncHttpGet(url2);
        
        // req3 success or throw error (promise reject)
        let res3 = await asyncHttpGet(url3);
        
        // 三个异步请求都成功 获取最终结果
        return [res1, res2, res3].join("\n")
    } catch(err) {
        // 出现错误，做一些处理
        console.log(err)
        throw err
    }
}

// 如此 3 个 Promise 请求在 async/await 的封装下变成了一个同步书写风格的异步请求
getUrls(url, url, url).then(res => {
    console.log(res)
    // todo 业务
}).catch(err => {
    console.log(err)
})

console.log("request has been sended, and waiting for res")
```



async 返回的是 `Promise`对象，所以我们还可以继续使用 `async\await`封装异步到同步风格。

```js
async function getUrlsMore(url1, url2) {
    try {
        let getUrls1 = await getUrls(url1, url1, url1)
        let getUrls2 = await getUrls(url2, url2, url2)
        
        // Promise resolve
        return [getUrls1, getUrls2].join("\n")
    } catch (err) {
        // Promise reject
        throw err
    }
}

getUrlsMore(url, url).then(res => {
    console.log(res)
}).catch(err => {
    console.log(err)
})
```



**async/await 和 Promise 的关系**

`async/await` 和 `Promise` 的关系非常的巧妙，`await`必须在`async`内使用，并装饰一个`Promise`对象，`async`返回的也是一个`Promise`对象。

`async/await`中的`return/throw`会代理自己返回的`Promise`的`resolve/reject`，而一个`Promise`的`resolve/reject`会使得`await`得到返回值或抛出异常。

如果方法内无`await`节点

`return` 一个`字面量`则会得到一个`{PromiseStatus: resolved}`的`Promise`。
`throw` 一个`Error`则会得到一个`{PromiseStatus: rejected}`的`Promise`。

如果方法内有`await`节点
`async`会返回一个`{PromiseStatus: pending}`的`Promise`（发生切换，异步等待`Promise`的执行结果）。
`Promise`的`resolve`会使得`await`的代码节点获得相应的返回结果，并继续向下执行。
`Promise`的`reject` 会使得`await`的代码节点自动抛出相应的异常，终止向下继续执行。



总结：async封装Promise，await相当then，try…catch相当于catch

**async 函数是什么**:

***async 函数，就是 Generator 函数的语法糖。*** 它有以下几个特点：

- 建立在promise之上。所以，不能把它和回调函数搭配使用。但它会声明一个异步函数，并隐式地返回一个Promise。因此可以直接return变量，无需使用Promise.resolve进行转换。
- 和promise一样，是非阻塞的。但不用写 then 及其回调函数，这减少代码行数，也避免了代码嵌套。而且，所有异步调用，可以写在同一个代码块中，无需定义多余的中间变量。
- 它的最大价值在于，可以使异步代码，在形式上，更接近于同步代码。
- 它总是与await一起使用的。并且，await 只能在 async 函数体内。
- await 是个运算符，用于组成表达式，它会阻塞后面的代码。如果等到的是 Promise 对象，则得到其 resolve值。否则，会得到一个表达式的运算结果。



```js
async function fn(args) {
    // ...
}

// 等同于
function fn(args) {
    return spawn(function*() {
        // ...
    });
}
```

**async 相较于 Promise的优势**

**中间值**： 没有多余的中间值，更加优雅地实现了。



**如果一个 Promise 被传递给一个 await 操作符，await 将等待 Promise 正常处理完成并返回其处理结果。**



##### JS two pillars

Prototypal Inheritance: Objects without classes, and prototype delegation, (Objects Linking to Other Objects)

Fucntional Programming: enbaled lambdas with closure



constructors downside:

1. not in strict mode can be dangerous
2. if you return an arbitrary object from a constructor function, it will break your prototype links, and the 'this' keyword will no longer be bound to the new object instance in the constructor. It is also less flexible than a real factory function because you cannot use this at all in the factory
3. It actually not important to have constructor functions because any function can return a new object. With dynamic object extension, object literals and `Object.create()` 



In JS, **factory functions** are simply constructor functions minus the 'new' requirement, global pollution danger and awkward limitations.

you can copy/extend object properties using object spread syntax: `{...a, ...b}`

The copy mechanism is another form of prototypal inheriatance. Sources of clone properties are a specific kind pof prototype called **exemplar prototypes**, and cloning an exemplar prototype is known as **concatenative inheritance**

Concatenative inheritance is possible because of a feature in JavaScript known as **dynamic object extension:** the ability to add to an object after it has been instantiated.

```
“Program to an interface, not an implementation,”
“favor object composition over class inheritance.”
```



##### Object Composition

Class inheritance accomplishes reuse by abstracting a common interface away into a base class that subclasses can inherit from, add to, and override. There are two important parts of abstraction:

- Generalization: The process of extracting only the shared properties and behaviors that serve the general use case
- Specialization: The process oof providing the implementation details required to serve the special case



##### 哈希路由

在 js 中，有一种方法，可以在不刷新页面的情况下，页面的内容进行变更，就是 哈希路由原理

先看一个简单的路由和页面内容关联的例子，要实现两个功能：

- 浏览器的路由变化，页面内容跟着变化
- 页面内容变换，浏览器的内容跟着变化



实现过程：

1. 设定一个页面按钮，点击按钮时，改变页面的内容
2. 设定浏览器的内容，跟随页面内容的变化而变化，即：直接赋值给浏览器的hash属性就可以了
3. 监听浏览器的hash值，如果hsah改变了，则页面内容跟随变化



##### 说一下Commonjs、AMD, CMD, ES6 modules

一个模块是能实现特定功能的文件，有了模块就可以方便的使用别人的代码，想要什么功能就能加载什么模块。

Commonjs：

暴露模块使用`module.exports` 和 `exports` 

全局性方法 `require()` 用于加载模块

Example：

```javascript
var math = require('math');
math.add(2, 3);
```

由于一个重大的局限，使得CommonJS规范不适用于浏览器环境。还是上一节的代码，如果在浏览器中运行，会有一个很大的问题: 第二行math.add(2, 3)，在第一行require(‘math’)之后运行，因此必须等math.js加载完成。也就是说，如果加载时间很长，整个应用就会停在那里等。

这对服务器端不是一个问题，因为所有的模块都存放在本地硬盘，可以同步加载完成，等待时间就是硬盘的读取时间。但是，对于浏览器，这却是一个大问题，因为模块都放在服务器端，等待时间取决于网速的快慢，可能要等很长时间，浏览器处于”假死”状态。 因此，浏览器端的模块，不能采用”同步加载”（synchronous），只能采用”异步加载”（asynchronous）。这就是AMD规范诞生的背景。



AMD (Asynchronous Module Definition) ：中文名异步模块定义的意思。采用异步方式加载模块，模块的加载不影响它后面语句的运行。所有依赖这个模块的语句，都定义在一个回调函数中，等到加载完成之后，这个回调函数才会运行。

模块必须采用特定的define()函数来定义:

`define(id?, dependencies?, factory)`

- id:字符串，模块名称(可选)
- dependencies: 是我们要载入的依赖模块(可选)，使用相对路径。,注意是数组格式
- factory: 工厂方法，返回一个模块函数

requireJS实现了AMD规范，主要用于解决下述两个问题。

1.多个文件有依赖关系，被依赖的文件需要早于依赖它的文件加载到浏览器

2.加载的时候浏览器会停止页面渲染，加载文件越多，页面失去响应的时间越长。

语法：requireJS定义了一个函数define，它是全局变量，用来定义模块。

```js
define(['dependency'], function(){
  var name = 'Byron';
  function printName(){
    console.log(name);
  }
  return {
    printName: printName
  };
});
```

加载模块

```
require(['myModule'], function (my){
	my.printName();
}
```

AMD也采用require()语句加载模块，但是不同于CommonJS，它要求两个参数：

`require([module],  callback)；`

总结AMD规范：require（）函数在加载依赖函数的时候是异步加载的，这样浏览器不会失去响应，它指定的回调函数，只有前面的模块加载成功，才会去执行。
因为网页在加载js的时候会停止渲染，因此我们可以通过异步的方式去加载js,而如果需要依赖某些，也是异步去依赖，依赖后再执行某些方法。

主要有两个Javascript库实现了AMD规范：[require.js](http://requirejs.org/)和[curl.js](http://cujojs.com/)。



**CMD规范**

CMD (Common Module Definition), 是seajs推崇的规范，CMD则是依赖就近，用的时候再require。它写起来是这样的：

```javascript
define(function(require, exports, module) {
  var clock = require('clock');
  clock.start();
});
```

CMD与AMD一样，也是采用特定的define()函数来定义,用require方式来引用模块:

`define(id?, dependencies?, factory)`

- id:字符串，模块名称(可选)
- dependencies: 是我们要载入的依赖模块(可选)，使用相对路径。,注意是数组格式
- factory: 工厂方法，返回一个模块函数

AMD和CMD最大的区别是对依赖模块的执行时机处理不同，而不是加载的时机或者方式不同，二者皆为异步加载模块。

AMD依赖前置，js可以方便知道依赖模块是谁，立即加载；

而CMD就近依赖，需要使用把模块变为字符串解析一遍才知道依赖了那些模块，这也是很多人诟病CMD的一点，牺牲性能来带来开发的便利性，实际上解析模块用的时间短到可以忽略。



**ES6 Modules**

ES6标准发布后，module成为标准，标准使用是以export指令导出接口，以import引入模块，但是在我们一贯的node模块中，我们依然采用的是CommonJS规范，使用require引入模块，使用module.exports导出接口。

**export 导出模块**

export语法声明用于导出函数、对象、指定文件（或模块）的原始值。

> 注意：在node中使用的是exports,不要混淆了

export有两种模块导出方式：**命名式导出（名称导出）**和**默认导出（定义式导出）**，命名式导出每个模块可以多个，而默认导出每个模块仅一个。

**命名式导出**:

模块可以通过export前缀关键词声明导出对象，导出对象可以是多个。这些导出对象用名称进行区分，称之为命名式导出。

```js
export { myFunction }; // 导出一个已定义的函数
export const foo = Math.sqrt(2); // 导出一个常量

// 我们可以使用*和from关键字来实现的模块的继承：
export * from 'article';

// 模块导出时，可以指定模块的导出成员。导出成员可以认为是类中的公有对象，而非导出成员可以认为是类中的私有对象：
var name = 'IT笔录';
var domain = 'http://itbilu.com';
 
export {name, domain}; // 相当于导出 {name:name,domain:domain}

// 模块导出时，我们可以使用as关键字对导出成员进行重命名：
var name = 'IT笔录';
var domain = 'http://itbilu.com';
 
export {name as siteName, domain};

```

**默认导出**:

默认导出也被称做定义式导出。命名式导出可以导出多个值，但在在import引用时，也要使用相同的名称来引用相应的值。而默认导出每个导出只有一个单一值，这个输出可以是一个函数、类或其它类型的值，这样在模块import导入时也会很容易引用。

```js
export default function() {}; // 可以导出一个函数
export default class(){}; // 也可以出一个类
```

**import 引入模块**:

import语法声明用于从已导出的模块、脚本中导入函数、对象、指定文件（或模块）的原始值。

import模块导入与export模块导出功能相对应，也存在两种模块导入方式：命名式导入（名称导入）和默认导入（定义式导入）



**命名式导入**: 我们可以通过指定名称，就是将这些成员插入到当作用域中。导出时，可以导入单个成员或多个成员：

```js
// 注意，花括号里面的变量与export后面的变量一一对应
import {myMember} from "my-module";
import {foo, bar} from "my-module";

// 通过*符号，我们可以导入模块中的全部属性和方法。当导入模块全部导出内容时，就是将导出模块（’my-module.js’）所有的导出绑定内容，插入到当前模块（’myModule’）的作用域中：
import * as myModule from "my-module";

// 导入模块对象时，也可以使用as对导入成员重命名，以方便在当前模块内使用：
import {reallyReallyLongModuleMemberName as shortName} from "my-module";

// 导入多个成员时，同样可以使用别名：
import {reallyReallyLongModuleMemberName as shortName, anotherLongModuleName as short} from "my-module";

// 导入一个模块，但不进行任何绑定：
import "my-module";

```

**默认导入**: 在模块导出时，可能会存在默认导出。同样的，在导入时可以使用import指令导出这些默认值。

```js
// 直接导入默认值：
import myDefault from "my-module";

// 也可以在命名空间导入和名称导入中，同时使用默认导入
import myDefault, * as myModule from "my-module"; // myModule 做为命名空间使用
import myDefault, {foo, bar} from "my-module"; // 指定成员导入
```

自 ES6 起，引入了一套新的 ES6 Module 规范，在语言标准的层面上实现了模块功能，而且实现得相当简单，有望成为浏览器和服务器通用的模块解决方案。但目前浏览器对 ES6 Module 兼容还不太好，我们平时在 Webpack 中使用的 export 和 import，会经过 Babel 转换为 CommonJS 规范。在使用上的差别主要有：

1. CommonJS 模块输出的是一个值的拷贝，ES6 模块输出的是值的引用。
2. CommonJS 模块是运行时加载，ES6 模块是编译时输出接口。
3. CommonJs 是单个值导出，ES6 Module可以导出多个
4. CommonJs 是动态语法可以写在判断里，ES6 Module 静态语法只能写在顶层
5. CommonJs 的 this 是当前模块，ES6 Module的 this 是 undefined



##### ES6 （https://www.taniarascia.com/es6-syntax-and-feature-overview/）

**Arrow Function**:

An **arrow function expression** is a compact alternative to a traditional [function expression](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/function), but is limited and can't be used in all situations.

**Differences & Limitations:**

- Does not have its own bindings to [`this`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this) or [`super`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/super), and should not be used as [`methods`](https://developer.mozilla.org/en-US/docs/Glossary/Method).
- Does not have [`new.target`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/new.target) keyword.
- Not suitable for [`call`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/call), [`apply`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/apply) and [`bind`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Function/bind) methods, which generally rely on establishing a [scope](https://developer.mozilla.org/en-US/docs/Glossary/Scope).
- Can not be used as [constructors](https://developer.mozilla.org/en-US/docs/Glossary/Constructor).
- Can not use [`yield`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/yield), within its body.

**Method definition shorthand**:

The `function` keyword can be omitted when assigning methods on an object.

```js
// ES5
var obj = {
  a: function (c, d) {},
  b: function (e, f) {},
}

// ES6
let obj = {
  a(c, d) {},
  b(e, f) {},
}

```

**Destructuring**:

Use curly brackets to assign properties of an object to their own variable.

```js
// ES5:
var a = obj.a
var b = obj.b
var c = obj.c

//ES6:
let {a, b, c} = obj
```



**Classes/constructor functions**:

ES6 introducess the `class` syntax on top of the prototype-based constructor function.

```js
// ES5:
function Func(a, b) {
  this.a = a
  this.b = b
}

Func.prototype.getSum = function () {
  return this.a + this.b
}

var x = new Func(3, 4)

// ES6:
class Func {
  constructor(a, b) {
    this.a = a
    this.b = b
  }

  getSum() {
    return this.a + this.b
  }
}

let x = new Func(3, 4)
```

**Inheritance**:

The `extends` keyword creates a subclass.

```js
// ES5:
function Inheritance(a, b, c) {
  Func.call(this, a, b)

  this.c = c
}

Inheritance.prototype = Object.create(Func.prototype)
Inheritance.prototype.getProduct = function () {
  return this.a * this.b * this.c
}

var y = new Inheritance(3, 4, 5)

// ES6:
class Inheritance extends Func {
  constructor(a, b, c) {
    super(a, b)

    this.c = c
  }

  getProduct() {
    return this.a * this.b * this.c
  }
}

let y = new Inheritance(3, 4, 5)
```























