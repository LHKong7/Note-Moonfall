# 62 UniquePaths



### 动态规划：

我们用 f（i，j）表示从左上角到 （i，j）的路径数量，其中 i 和 j 的范围分别是 【0，m） 和 【0， n）



由于我们每一步只能从向下或者向右移动一步，因此要想走到 (i, j)，

- 如果向下走一步，那么会从 (i-1, j) 走过来；
- 如果向右走一步，那么会从 (i, j-1) 走过来

```
f(i,j) = f(i−1,j) + f(i,j−1)
```



```javascript
/**
 * @param {number} m
 * @param {number} n
 * @return {number}
 */
var uniquePaths = function(m, n) {
    let dp = new Array(m).fill(0).map(() => new Array(n).fill(0));

    for (let i = 0; i < m; i++) dp[i][0] = 1;
    for (let i = 0; i < n; i++) dp[0][i] = 1;

    for (let i = 1; i < m; i++) {
        for (let j = 1; j < n; j++) {
            dp[i][j] = dp[i-1][j] + dp[i][j-1];
        }
    }

    return dp[m-1][n-1];
};

```





