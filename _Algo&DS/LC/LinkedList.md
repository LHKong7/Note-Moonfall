# Linked List Related

### 237 删除链表中的节点
```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val) {
 *     this.val = val;
 *     this.next = null;
 * }
 */
/**
 * @param {ListNode} node
 * @return {void} Do not return anything, modify node in-place instead.
 */
var deleteNode = function(node) {
    node.val = node.next.val;
    node.next = node.next.next;
};
```

### 83 删除排序链表中的重复元素

**Solution**: 
    使用两个指针，prev指针指向head， curr指针指向 head.next
    当两个值相等的话：说明重复，将prev 指针的下一个 指向 curr.next，并且将 curr.next 指针指向 null 用来删除当前node
    如果不想等： prev 变为 curr

    每次遍历 curr = prev.next


```javascript
/**
 * Definition for singly-linked list.
 * function ListNode(val, next) {
 *     this.val = (val===undefined ? 0 : val)
 *     this.next = (next===undefined ? null : next)
 * }
 */
/**
 * @param {ListNode} head
 * @return {ListNode}
 */
var deleteDuplicates = function(head) {
    if (!head || !head.next) return head;

    let prev = head, curr = head.next;

    while (curr !== null) {
        if (prev.val === curr.val) {
            prev.next = curr.next;
            curr.next = null;
        } else {
            prev = curr;
        }

        curr = prev.next;
    }

    return head;
};
```

