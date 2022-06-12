## LinkedList



##### 指针/引用

数据加载进内存

内存是有地址的



JVM： 

​	栈内存：变量

​	堆内存： 



##### 为什么需要链表

解决问题：链表不需要连续的内存空间，可以充分的利用内存空间

数组：线性表结构，用一组连续的内存空间，来存储遇阻具有相同类型的数据。数组是一组静态的数据结构

非连续的内存空间使用不充分，怎么访问分布在非连续内存空间

链表是动态数据结构，天然的支持动态扩容

存在相同数量的数据时，链表需要的内存空间比数组大，存储当前数据的值+下一个数据的地址



##### 节点表示

头节点：用来记录链表的基地址

尾节点：用来表示链表的最后一个节点

##### 链表

**索引概念**：索引从0开始，头节点是索引开始。

```java
Node curr = head
curr = curr.next;
```

索引和size的关系：size的值比最大的索引值+1，指向null



添加头节点：

 1. 链表的表头

    创建新节点，新节点的next是head

    ```java
    Node node = new Node(22);
    node.next = head
    head = node
    ```

    

 2. 链表的中间，添加节点

    1. Init 节点
    2. 找到插入节点位置的前一个节点 记录prev 前一个节点 （从表头一个一个找）
    3. node.next = prev.next
    4. prev.next = node

    

    

    删除头节点

    ```java
    Node delNode = head
    head = head.next
    delNode.next = null
    ```

    删除中间节点

    1. 找到删除节点的prev节点 （从链表头遍历）
    2. 临时存储待删除的节点 Node delNode = prev.next
    3. prev.next = delNode.next
    4. delNode.next = null

    

    

    ##### 哨兵节点 （虚拟节点）

    dummyHead在链表最前面，使“前”头节点变成中间节点处理逻辑一样

    

    

    时间空间复杂度：

    

    Get：TIME：  O（n） SPACE：O（1）

    Get First： Time O（1）

    

    修改：表尾：O（n）

    

    add：TIME：O（n）

    remove：Time： O（n）

    

    CRUD： all O（n） 表头：O（1）

    

    

    ### 双向链表

    

    next指向下一个节点的prev

    prev指向上一个节点的next

    记录first节点和last节点

    

    

    优缺点：

    缺点： 浪费内存

    

    优点

    ​	查询index=1的节点 index < size/2 从first开始遍历查询

    ​	查询 index > size/2 从last开始遍历查询

    遍历链表的一半

    时间复杂度：O（n/2）=》 O（n）

    first和last都是O（1）

    

    插入节点：

    ​	1. initNode 

    

    

    

    ##### 链表的算法

    基础算法

    快慢指针

    链表排序

    

    

    

    

    

    

    

    

    

    

    

    

    

    

    





















