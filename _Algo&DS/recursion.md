# Recursion



## Basic Knowledge

All recursive algorithms must have the following:

- Base Case (when to stop)
- Work toward Base Case
- Recursive Call (call ourselves)

The "work toword base case" is where we make the problem simpler. The recursive call, is where we use the same algo to solve a simpler version of the problem. The base case is the solution to the "simplest" possible problem



## Why Recursion Works

In a recursive algorithm, the computer "remembers" every previous state of the problem. This information is "held" by the computer on a **"activation stack"** (i.e. inside of each function workspace)

Every function has its own workspace PER CALL of the function.



##### 方法调用系统栈

方法调用符合后进先出

栈帧：方法参数x和y，局部变量temp 和 返回地址



##### 方法调用本身

需要退出条件

方法调用本身的意义： 解决特定问题

1. 计算1-n之和

递归程序的特点：

1. 大问题可以拆解成多个子问题
2. 每一个子问题解决方法与大问题解决方法一样
3. 存在终止条件 （最小子问题已知）



递归代码也是很好写的：
\1. 写出递推公式
\2. 写出递归终止条件













