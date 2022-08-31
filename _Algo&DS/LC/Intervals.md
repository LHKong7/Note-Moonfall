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







