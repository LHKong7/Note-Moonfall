# React Interview Questions



## TODO:

	- https://blog.csdn.net/eyeofangel/article/details/88797314
	- https://www.jianshu.com/p/1859224e4d79

##### **区分Real DOM和Virtual DOM**

Real DOM	Virtual DOM
1. 更新缓慢。	1. 更新更快。
2. 可以直接更新 HTML。	2. 无法直接更新 HTML。
3. 如果元素更新，则创建新DOM。	3. 如果元素更新，则更新 JSX 。
4. DOM操作代价很高。	4. DOM 操作非常简单。
5. 消耗的内存较多。	5. 很少的内存消耗。



##### 什么是Virtual DOM

DOM结构是一系列的属性和方法的集合。所谓Virtual DOM，就是用轻量级的JavaScript对象来代替庞杂的DOM结构。下面代码就展示了HTML结构和Virtual DOM之间的关系。



##### diff算法

不管是DOM还是虚拟DOM，它们的结构都是一棵树，完全对比两棵树变化的算法时间复杂度是O(n^3)，但是考虑到我们很少会跨层级移动DOM，所以我们只需要对比同一层级的变化。

总而言之，我们的diff算法有两个原则：

- 对比当前真实的DOM和虚拟DOM，在对比过程中直接更新真实DOM
- 只对比同一层级的变化

虚拟DOM的结构可以分为三种，分别表示文本、原生DOM节点以及组件。

https://github.com/hujiulong/blog/issues/6

**diff策略**
 React用 三大策略 将O(n^3)复杂度 转化为 **O(n)复杂度**

策略一（**tree diff**）：
 Web UI中DOM节点跨层级的移动操作特别少，可以忽略不计。

策略二（**component diff**）：
 拥有相同类的两个组件 生成相似的树形结构，
 拥有不同类的两个组件 生成不同的树形结构。

策略三（**element diff**）：
 对于同一层级的一组子节点，通过唯一id区分。



**tree diff**
 （1）React通过updateDepth对Virtual DOM树进行**层级控制**。
 （2）对树分层比较，两棵树 只对**同一层次节点** 进行比较。如果该节点不存在时，则该节点及其子节点会被完全删除，不会再进一步比较。
 （3）只需遍历一次，就能完成整棵DOM树的比较。

**那么问题来了，如果DOM节点出现了跨层级操作,diff会咋办呢？**
答：diff只简单考虑同层级的节点位置变换，如果是跨层级的话，**只有创建节点和删除节点的操作。**

以A为根节点的整棵树会被**重新创建，而不是移动**，因此 **官方建议不要进行DOM节点跨层级操作，可以通过CSS隐藏、显示节点，而不是真正地移除、添加DOM节点**。



**component diff**
 React对不同的组件间的比较，有三种策略
 （1）同一类型的两个组件，按原策略（层级比较）继续比较Virtual DOM树即可。

（2）同一类型的两个组件，组件A变化为组件B时，可能Virtual DOM没有任何变化，如果知道这点（变换的过程中，Virtual DOM没有改变），可节省大量计算时间，所以 用户 可以通过 **shouldComponentUpdate()** 来判断是否需要 判断计算。

（3）不同类型的组件，将一个（将被改变的）组件判断为dirty component（脏组件），从而**替换 整个组件的所有节点**。

**element diff**
 当节点处于同一层级时，diff提供三种节点操作：**删除、插入、移动**。

**插入**：组件 C 不在集合（A,B）中，需要插入

**删除**：（1）组件 D 在集合（A,B,D）中，但 D的节点已经更改，不能复用和更新，所以需要**删除 旧的 D** ，再创建新的。

（2）组件 D 之前在 集合（A,B,D）中，但集合变成新的集合（A,B）了，D 就需要被删除。

**移动**：组件D已经在集合（A,B,C,D）里了，且集合更新时，D没有发生更新，只是位置改变，如新集合（A,D,B,C），D在第二个，无须像传统diff，让旧集合的第二个B和新集合的第二个D 比较，并且删除第二个位置的B，再在第二个位置插入D，而是 **（对同一层级的同组子节点） 添加唯一key进行区分，移动即可。**

https://www.jianshu.com/p/3ba0822018cf



https://www.jianshu.com/p/1859224e4d79



https://react.jokcy.me/book/api/react.html



**tree diff**

只会对同一层次的节点进行比较，如果节点不存在直接删除创建

**Component diff**

同一类型的组件继续tree diff比较，不同类型的组件直接删除重建。

**element diff 或者叫list diff**
三种方法：插入，移动，删除

INSERT_MARKUP插入，新的 component 类型不在老集合里， 即是全新的节点，需要对新节点执行插入操作。

MOVE_EXISTING移动，在老集合有新 component 类型，且 element 是可更新的类型，generateComponentChildren 已调用 receiveComponent，这种情况下 prevChild=nextChild，就需要做移动操作，可以复用以前的 DOM 节点。

REMOVE_NODE删除，老 component 类型，在新集合里也有，但对应的 element 不同则不能直接复用和更新，需要执行删除操作，或者老 component 不在新集合里的，也需要执行删除操作。



React 通过制定大胆的 diff 策略，将 O(n3) 复杂度的问题转换成 O(n) 复杂度的问题；

React 通过分层求异的策略，对 tree diff 进行算法优化；

React 通过相同类生成相似树形结构，不同类生成不同树形结构的策略，对 component diff 进行算法优化；

React 通过设置唯一 key的策略，对 element diff 进行算法优化；

建议，在开发组件时，保持稳定的 DOM 结构会有助于性能的提升；

建议，在开发过程中，尽量减少类似将最后一个节点移动到列表首部的操作，当节点数量过大或更新操作过于频繁时，在一定程度上会影响 React 的渲染性能。








