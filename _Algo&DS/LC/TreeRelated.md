## InOrder Traversal

左-根-有

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var inorderTraversal = function(root) {
    let res = [];
    const inOrder = (node) => {
        if (node === null) return;

        inOrder(node.left);
        res.push(node.val);
        inOrder(node.right);
    }

    inOrder(root);
    return res;
};


/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number[]}
 */
var inorderTraversal = function(root) {
    let res = [], stk = [];

    while (root || stk.length) {
        while (root) {
            stk.push(root);
            root = root.left;
        }

        root = stk.pop();
        res.push(root.val);
        root = root.right;
    }

    return res;
};
```





## 687 longestUnivaluePath

**题目描述**:

给定一个二叉树的 root ，返回 最长的路径的长度 ，这个路径中的 每个节点具有相同值 。 这条路径可以经过也可以不经过根节点。 两个节点之间的路径长度 由它们之间的边数表示。

```
输入：root = [5,4,5,1,1,5]
输出：2
```

我们将二叉树看成一个有向图（从父结点指向子结点的边），定义同值有向路径为从某一结点出发，到达它的某一后代节点的路径，且经过的结点的值相同。最长同值路径长度 	= 	某一节点的	左最长同值有向路径长度 + 右最长同值有向路径长度。



针对每一个node，我们分别获取 左节点的 最长同值路径长度 left， 右节点 的最长同值有向路径长度 right。

如果节点 root 的左 最长同值有向路径长度 left1 = left + 1, otherwise left1 = 0

如果结点 *root* 的右结点非空且结点 *root* 的值与它的右结点的值相等. 那么结点 root 的 右最长同值有向路径长度 right1 = right + 1 ,otherwise right1 = 0

令 ` res = math.max(res, left1+right)`

并且返回结点 *root* 对应的最长同值有向路径长度 `math.max(left1, right1)`

```js
/**
 * Definition for a binary tree node.
 * function TreeNode(val, left, right) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.left = (left===undefined ? null : left)
 *     this.right = (right===undefined ? null : right)
 * }
 */
/**
 * @param {TreeNode} root
 * @return {number}
 */
var longestUnivaluePath = function(root) {
    if (root === null) return 0;
    let res = Number.MIN_SAFE_INTEGER;

    const dfs = (node) => {
        if (node === null) return 0;

        let left = dfs(node.left), right = dfs(node.right);
        let left1 = 0, right1 = 0;
        if (node.left && node.left.val === node.val) left1 = left+1;
        if (node.right && node.right.val === node.val) right1 = right+1;

        res = Math.max(res, left1 + right1);
        return Math.max(left1, right1)
    }

    dfs(root);

    return res;
};
```















