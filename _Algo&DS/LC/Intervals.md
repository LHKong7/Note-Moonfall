# 插入区间



对于区间列表里面的两个区间（A，B）来说，共有4种情况：

1. 当A区间的较大值 A-RightNumber <  B-leftNumber B区间的较小值 : A区间在B区间的左侧
2. 当A区间的较小值 A-LeftNumber > B-RightNumber B区间的较大值 : A区间在B区间的右侧

如果上述情况都不满足 说明A区间与B区间有交集或者并集合：

- 交集：`[max(A_L1,BL_2),min(A_R1,B_R2)]`

- 并集：`[min(A_L1,B_L2),max(A_R1,B_R2)]`



给你一个 **无重叠的** *，*按照区间起始端点排序的区间列表。

在列表中插入一个新的区间，你需要确保列表中的区间仍然有序且不重叠（如果有必要的话，可以合并区间）。

```
输入：intervals = [[1,3],[6,9]], newInterval = [2,5]
输出：[[1,5],[6,9]]
```



### Solution

在给定区间集合 X 互不重叠的情况下， 当插入一个新的区间时，

- 找出所有与区间S 重叠的集合区间 X‘
- 将 X’ 中的所有区间连带上区间S 合并成一个大区间



遍历区间数组 当遍历到 【L<sub>i</sub> ， R<sub>i</sub> 】时：

- 如果 Ri < left 说明 这个遍历到的区间与 插入区间不重叠 并在插入区间的左侧
- 如果 Li > right 说明 这个遍历到的区间与 插入区间不重叠 并在插入区间的左侧 
- 如果 上述两种情况不满足，说明 遍历到的区间与插入区间有重叠 我们只需要 合并两个区间 使其变为 插入区间即可 



```javascript
/**
 * @param {number[][]} intervals
 * @param {number[]} newInterval
 * @return {number[][]}
 */
var insert = function(intervals, newInterval) {
    let [left, right] = newInterval;
    let placed = false;
    let res = [];

    for (let [leftLow, rightHigh] of intervals) {
        if (leftLow > right) {
            if (!placed) {
                res.push([left, right]);
                placed = true;
            }
            res.push([leftLow, rightHigh]);
        } else if (rightHigh < left) {
            res.push([leftLow, rightHigh]);
        } else {
            left = Math.min(left, leftLow);
            right = Math.max(right, rightHigh);
        }
    }

    if (!placed) {
        res.push([left, right]);
    }

    return res;
};

let res = insert(
    [[1,3],[6,9]],
    [2,5]
)
console.log("res of insert new Intervals: ", res);
```







# 56_ 合并区间

先给区间进行排序（区间的第一个元素）， 

遍历区间数组，分情况合并两个区间：

- 当 res数组中无元素 或者 res数组中最后一个元素的 第二个值（区间较大值） `<` 遍历到的区间的较小值时，直接将区间数组放到res中
- 其他情况，合并数组， 直接修改res数组中的最后一个区间的大区间 `=`  `Math.max(res[res.length-1][1], intervals[i][1])`



```javascript
/**
 * @param {number[][]} intervals
 * @return {number[][]}
 */
var merge = function(intervals) {
    let res = [];

    intervals.sort((a, b) => {
        return a[0] - b[0];
    })

    for (let i = 0; i < intervals.length; i++) {
        if (!res[res.length-1] || res[res.length-1][1] < intervals[i][0]) {
            res.push(intervals[i]);
        } else {
            res[res.length-1][1] = Math.max(res[res.length-1][1], intervals[i][1]);
        }
    }

    return res;
};
```



### 435 无重叠区间

给定一个区间的集合 intervals ，其中 intervals[i] = [starti, endi] 。返回 需要移除区间的最小数量，使剩余区间互不重叠 。

「选出最多数量的区间，使得它们互不重叠」

由于选出的区间互不重叠，因此我们可以将它们按照端点从小到大的顺序进行排序，并且无论我们按照左端点还是右端点进行排序，得到的结果都是唯一的。



**Solution 1: ** 我们可以先将所有的 n*n* 个区间按照左端点（或者右端点）从小到大进行排序，随后使用动态规划的方法求出区间数量的最大值。令 f<sub>i </sub>表示「以区间 i为最后一个区间，可以选出的区间数量的最大值」

```
for i = 1; i < length; i++
	for j = 0; j < i; j++
```

判断重叠，当 j 区间的最右端点 <= i 区间的最左端点时 两个区间没有重叠。



**Solution 2**: 贪心

我们可以不断地寻找右端点在首个区间右端点左侧的新区间，将首个区间替换成该区间。那么当我们无法替换时，首个区间就是所有可以选择的区间中右端点最小的那个区间。因此我们将所有区间按照右端点从小到大进行排序，那么排完序之后的首个区间，就是我们选择的首个区间。



如果有多个区间的右端点都同样最小怎么办？由于我们选择的是首个区间，因此在左侧不会有其它的区间，那么左端点在何处是不重要的，我们只要任意选择一个右端点最小的区间即可。

当确定了首个区间之后，所有与首个区间不重合的区间就组成了一个规模更小的子问题。由于我们已经在初始时将所有区间按照右端点排好序了，因此对于这个子问题，我们无需再次进行排序，只要找出其中与首个区间不重合并且右端点最小的区间即可。用相同的方法，我们可以依次确定后续的所有区间。

在实际的代码编写中，我们对按照右端点排好序的区间进行遍历，并且实时维护上一个选择区间的右端点 right。如果当前遍历到的区间 如果当前遍历到的区间 【Li, ri】与上一个区间不重合 即 li >= right. 那么我们就可以贪心地选择这个区间，并将 *right* 更新为 ri

### 646 最长数对链

这题和「435. 无重叠区间」类似，区别就是：

此题中，数对链中相邻的数对，前者的第二个数字必须小于后者的第一个数字。而在「435. 无重叠区间」中，相邻的区间，前者的结束时间需小于等于后者的开始时间。
此题返回最长数对链的长度，而 「435. 无重叠区间」返回形成无重叠区间，最少需要删除多少区间（即原长度减去最长数对链的长度）。






