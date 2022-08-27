# SOLID Design Principles 





##### The Single Responsibility Principle

**A class should have one, and only one, reason to change, not limited to classes, but also software components and microservices**

***Pros:***

- it makes the software easier to implement and prevents unexpected side-effects of future changes.
- Frequency and Effects of Changes: If the class implements multiple responsibilities, they are no longer independent of each other. It is better to avoid side effects problems by making sure that each class has only one responsibility
- Eaiser to Understand: Maximize the features of the single responsibility principle



##### Open/Closed Principle 

开闭原则 对扩展开放，对修改关闭。多个变化导致一处修改，则对变化的识别不准，容易考虑不周，修改引入。

**Software entities (classes, modules, functions, etc.) should be open for extension, but closed for modification**

The code should be able to add new functionality without changing the existing code. That prevents situations in which a change to one of your classes also requires you to adapt all depending classes.



**A class is closed, since it may be compiled, stored in a librarym baselined, and used by client classes. But it is also open, since any new class may use it as parent, adding new features. When a descendant class is defined, there is no need to change the original or to disturb its clients.**

It uses interfaces of superclasses to allow different implementations which you can easily substitute without changing the code that uses them. The interfaces are closed for modifications and you can provide new implementations to extend the functionality of the software.



The main benefit of this approach is that an interface introduces an additional level of abstraction which enables loose coupling. The implementations of an interface are independent of each other and don’t need to share any code.

If you consider it beneficial that two implementations of an interface share some code, you can either use [inheritance](https://stackify.com/oop-concept-inheritance/) or [composition](https://stackify.com/oop-concepts-composition/).





##### Liskov Substitution Principle

If S is a subtype of T, then objects of type T may be replaced with objects of type S

Composition: Adding a functionality instead of inheriting functionality







##### Interface Segregation Principle

break out the large interfaces or classes into smaller parts

In JS

`object.assign()`



##### Dependency Inversion

Add an interface into the middle of two components





