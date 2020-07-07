# [Day 38] Reverse Linked List Series

<a name="xUQGR"></a>
## 206. Reverse Linked List
<a name="K30he"></a>
#### Link
[https://leetcode.com/problems/reverse-linked-list/](https://leetcode.com/problems/reverse-linked-list/)
<a name="ddCzG"></a>
#### Solution
Method 1: Iterative
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
var reverseList = function(head) {
    if (!head || !head.next) return head
    let current = head
    let pre = null
    while (current) {
        const next = current.next
        current.next = pre
        pre = current
        current = next
    }
    return pre
}
```
Method 2: Recursive
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
var reverseList = function(head) {
    if (!head || !head.next) return head
    let newReverseList = reverseList(head.next)
    head.next.next = head
    head.next = null
    return newReverseList
}
```
<a name="Sz0Q9"></a>
#### Complexity
Iterative:

- Time Complexity: O(n) - n is the list's length
- Space Complexity: O(1)

Recursive:

- Time Complexity: O(n) - n is the list's length
- Space Complexity: O(n) - n levels deep of recursion stack



