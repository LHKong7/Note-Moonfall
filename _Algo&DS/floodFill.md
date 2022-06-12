### FloodFill



基础：

##### 二维数组转一位数组

​	col & row =》 array

下标索引转换公式：二维下标转成一位 

**i * col + j** ：

​	 i 表示行索引 

​	j 表示列索引 

​	cols 表示列数



##### 一维数组转成二维数组

遍历一维数组每一个元素，一维数组

​	行坐标： i = index / cols

​	列坐标： j = index % cols



#### 二维数组的四联通

top：行坐标-1 列坐标不变 [-1, 0]

bottom：行坐标+1， 列坐标不变 [1, 0]

left： 行坐标相同，列坐标-1 [0, -1]

right： 行坐标相同，列坐标+1 [0, 1]



```javascript
const dirs = [[-1, 0], [1, 0], [0, -1], [0, 1]]

for (dir of dirs) {
	let row = i + dir[0];
	let col = j + dir[1];
}
```





##### 二维数组的八联通

左上：[-1, -1] 

右上：[-1, 1]

左下：[1, -1]

右下：[1, 1]



##### 保证索引访问合法

row < rows (arr.length)

col < cols (arr[0].length)

row >= 0

col >= 0









