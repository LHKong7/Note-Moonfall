# 单调栈



##### 1475 商品折扣后的最终价格



单调栈中维护当前位置右边更小的元素列表，从栈底到栈顶的元素都是单调递增的。

​	每次移动到数组中一个新元素即为栈顶元素，如果栈为空则说明当前位置右边没有更大的元素，随后将位置i的元素入栈



遍历prices 元素 针对于每一个 prices[i]：

- 如果当前栈顶的元素大于 prices[i]，则将栈顶元素出栈，直到栈顶的元素小于等于 prices[i], 栈顶的元素即为右边第一个小于 prices[i] 的元素
- 如果当前栈顶的元素小于等于 prices[i]， 此时可以知道当前栈顶元素为 i 的右边第一个小于等于 prices[i] 的元素，此时第 i 个物品折后的价格为 prices[i] 与 栈顶的元素的差
- 如果当前栈中的元素为空，则此时折扣为 0，商品的价格为 原价 prices[i]
- 将 prices[i] 压入栈中，保证 prices[i] 为当前栈中的最大值



```js
/**
 * @param {number[]} prices
 * @return {number[]}
 */
var finalPrices = function(prices) {
    const n = prices.length;
    const finalPrices = [];
    const stack = [];

    for (let i = n - 1; i >= 0; i--) {
        while (stack.length && stack[stack.length-1] > prices[i]) {
            stack.pop();
        }

        const afterDiscount = stack.length === 0 ? prices[i] : prices[i] - stack[stack.length-1];
        stack.push(prices[i]);
        finalPrices.unshift(afterDiscount)
    }

    return finalPrices;
};
```







