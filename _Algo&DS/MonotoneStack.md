## 单调栈



单调栈就是指栈中的元素必须是按照升序排列的栈，或者是降序排列的栈



单调递增栈：里面的元素是升序排列



单调递减栈：里面的元素是降序排列



**应用**：

- 找出数组中右边第一个比我小的元素
- 找出数组中右边第一个比我大的元素
- 找出数组中左边离我最近比我小的元素
- 找出数组中左边离我最近比我大的元素



**WHY？**

减少时间复杂度 从O（n^2) -> 数组一次遍历 + 单调栈遍历一次 = O(2n) -> O(n)



```javascript
var dailyTemperatures = function(temperatures) {
    if (temperatures.length === 1) return [];
    const monoStk = [];
    const res = new Array(temperatures.length).fill(0);

    for (let i = 0; i < temperatures.length; i++) {
        let curr = temperatures[i];

        while (monoStk.length && temperatures[monoStk[monoStk.length - 1]] < curr) {
            let prevIdx = monoStk.pop();

            res[prevIdx] = i - prevIdx;
        }
        monoStk.push(i);
    }

    return res;
};
```

