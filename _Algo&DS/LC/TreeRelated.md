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

