

##### 订阅发布模式（Subscriber/publish）

订阅发布模式定义了一种一对多的依赖关系，让多个订阅者对象同时监听某一个主题对象。这个主题对象在自身状态变化时，会通知所有订阅者对象，使它们能够自动更新自己的状态。

​	将一个系统分割成一系列相互协作的类有一个很不好的副作用，那就是需要维护相应对象间的一致性，这样会给维护、扩展和重用都带来不便。当一个对象的改变需要同时改变其他对象，而且它不知道具体有多少对象需要改变时，就可以使用订阅发布模式了。

​	    一个抽象模型有两个方面，其中一方面依赖于另一方面，这时订阅发布模式可以将这两者封装在独立的对象中，使它们各自独立地改变和复用。订阅发布模式所做的工作其实就是在解耦合。让耦合的双方都依赖于抽象，而不是依赖于具体，从而使得各自的变化都不会影响另一边的变化。





##### Singleton Pattern

Database Driver

For a given class, there is only one object (Data Store) => State of app





##### Facade Pattern

Compiler



##### Bridge/Adapter Pattern



##### Strategy pattern



##### Observer Pattern

订阅发布模式（Subscriber/publish）MQ
