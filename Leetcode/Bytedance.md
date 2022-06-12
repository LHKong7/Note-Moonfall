##### Bytedance Review Questions



##### 402 removeKdigits

题目描述： 给你一个以字符串表示的非负整数 `num` 和一个整数 `k` ，移除这个数中的 `k` 位数字，使得剩下的数字最小。请你以字符串形式返回这个最小的数字。

```
num = 1432219
k = 3
res:	1219


num: 10200
k = 1
res : 200
```

数字比较: 对于两个相同长度的数字序列，最左边不同的数字决定了这两个数字的大小

删除一个数字的贪心策略：

- [D0D1D2 ... Dn-1] 从左往右找到第一个位置 i (i > 0) 使得Di < Di-1 => 删除Di-1
- 如果不存在Di < Di-1 说明序列递增，删除最后一个字符



##### 409 longestPalindrome

如果字符出现的是偶数：两边各放一半

如果字符出现的是奇数：要判断当前字符串，如果当前字符串是奇数 不能放 如果是偶数放在中间

贪心策略： 每次将字母的 v/2 v是出现的次数 放在回文串的左右两侧



##### 64 minPathSum

**BackTracking**:

从 [0, 0] 开始 向上 (1, 0)或向下(0, 1) 

构建树形结构 当到达 `(*row* === *grid*.length - 1 && *col* === *grid*[0].length - 1)` 到达叶子节点时，计算最小路径和

剪枝 `if (nextRow < 0 || nextCol < 0 || nextRow >= *grid*.length || nextCol >= *grid*[0].length) continue;` 

优化：记录每次到达叶子节点 在节点处取最小子节点的值

**memoization**

将每一个节点到叶子节点的最小路径和

Memo数组里存储的是当前节点到终点的最小路径和

**DP**:

`dp[i][j]` : 表示从 i，j 到右下角（终点）的最短路径

`dp[m-1][n-1] = grid[m-1][n-1]`

最后一行： `dp[m-1][j] = grid[m-1][j] + dp[m-1][j+1]`

最后一列： `dp[i][n-1] = grid[i][n-1] + dp[i+1][n-1]`

平常的状态转移: `dp[i][j] = grid[i][j] + min(dp[i-1][j], dp[i][j-1])`



##### 53 maxSubArray

```javascript
var maxSubArray = function(nums) {
    let pre = 0, maxAns = nums[0];
    nums.forEach((x) => {
        pre = Math.max(pre + x, x);
        maxAns = Math.max(maxAns, pre);
    });
    return maxAns;
};
```



##### 647 回文子串

**Dynamic Programming**:

定义状态： `dp[i][j]` 表示子数组区间 `[i, j]` 对应的子串是否是回文

如果 `s.charAt[i] === s.charAt[j]` 的话， 那么 `dp[i][j] = dp[i+1][j-1]`

如果 `s.charAt[i] !== s.charAt[j]` 的话， 那么 `dp[i][j] =false`

如果 只有两个字符的话， 那么`dp[i][j] = (s.charAt[i] == s.charAt[j])`

确定状态转移方向： 初始化都是false



##### 5 最长回文串

##### 131



##### 300 最长递增子序列

`dp[i]` 表示以索引为i的元素结尾的最长递增子序列的长度

`nums[j] > nums[i] : dp[j] = max(1 + dp[i], dp[i])`

`nums[j] <= nums[i] : dp[j] = 1 `



**最长递增子数组**：



##### 72 minDistance

求最优值问题：

状态定义： 对于字符串的定义用二维数组来表示

​	`dp[i][j]` 表示word1前i个字符转换成word2前j个字符 。 花的最少操作数 （即编辑距离）

​	`dp = new Array(word1.length + 1).fill(0).map(() => new Array(word2.length + 1).fill(0))`



状态推导：

当 `word.charAt(i-1) == word2.charAt(j-1)` 时 `dp[i][j] = dp[i-1][j-1]`

`dp[0][0`] 表示word1前0个字符转换成word2 前0个字符的编辑距离

前0个字符的意思就是空字符串的意思。



当 `word1.charAt(i) !== word2.charAt(j)`

插入： `1 + dp[i][j-1]`

删除： `1 + dp[i-1][j] `

替换：`1 + dp[i-1][j-1]`

最终： `1+min(dp[i][j-1], dp[i-1][j], dp[i-1][j-1])`



























