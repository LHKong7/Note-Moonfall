# 542 01矩阵

给定一个由 `0` 和 `1` 组成的矩阵`mat` ，请输出一个大小相同的矩阵，其中每一个格子是 `mat` 中对应位置元素到最近的 `0 `的距离。

两个相邻元素间的距离为 1 。

```
输入：mat = [[0,0,0],[0,1,0],[1,1,1]]
输出：[[0,0,0],[0,1,0],[1,2,1]]
```

对于二维数组中的每一个元素来说，

- 如果它的值为0，那么离它最近的0就是它自己。
- 如果它的值为1，那么我们就需要找出离它最近的0， 并且返回这个距离值。那么如何对于二维数组的每一个1，都快速找出离它最近的0呢

如果二维数组中只有一个0，那么对于每一个1，离它最近的0就是那个唯一的0 如何求出这个距离呢？

1. 如果0在二维数组中的位置是 我们可以通过计算0和1在水平方向的距离 + 竖直方向的距离，来求出0和1之间的距离
2. 我们可以从 0的位置开始进行 **广度优先搜索**。广度优先搜索可以找到从起点到其余所有点的 **最短距离**。 因此如果我们从 0 开始搜索，每次搜索到一个 1，就可以得到 0 到这个 1 的最短距离，也就离这个 1 最近的 0 的距离了（因为矩阵中只有一个 0）



第一种方法可行，但是二维数组中有不止一个0 这样的话，就必须对于每个1计算一次它到所有0的距离，再从中取一个最小值，时间复杂度会非常高



多源广度优先搜索，只是有多个源头

尽管有不止一个0，





广度优先搜索

