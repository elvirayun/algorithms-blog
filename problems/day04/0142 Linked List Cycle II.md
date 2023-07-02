# 142. Linked List Cycle II

## Problem

*****

Given the `head` of a linked list, return *the node where the cycle begins. If there is no cycle, return* `null`.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to (**0-indexed**). It is `-1` if there is no cycle. **Note that** `pos` **is not passed as a parameter**.

**Do not modify** the linked list.

 

**Example 1:**

![img](./0142%20Linked%20List%20Cycle%20II.assets/circularlinkedlist.png)

```
Input: head = [3,2,0,-4], pos = 1
Output: tail connects to node index 1
Explanation: There is a cycle in the linked list, where tail connects to the second node.
```

**Example 2:**

![img](./0142%20Linked%20List%20Cycle%20II.assets/circularlinkedlist_test2.png)

```
Input: head = [1,2], pos = 0
Output: tail connects to node index 0
Explanation: There is a cycle in the linked list, where tail connects to the first node.
```

**Example 3:**

![img](./0142%20Linked%20List%20Cycle%20II.assets/circularlinkedlist_test3.png)

```
Input: head = [1], pos = -1
Output: no cycle
Explanation: There is no cycle in the linked list.
```

 

**Constraints:**

- The number of the nodes in the list is in the range `[0, 104]`.
- `-105 <= Node.val <= 105`
- `pos` is `-1` or a **valid index** in the linked-list.

 

**Follow up:** Can you solve it using `O(1)` (i.e. constant) memory?	

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- [文字题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0142.环形链表II.md#其他语言版本)
- [视频题解](https://www.bilibili.com/video/BV1if4y1d7ob/)

[![img](./0142%20Linked%20List%20Cycle%20II.assets/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303232303932353130333433332e706e67.png)](https://camo.githubusercontent.com/74c0180eec6d7396d787acd1f237765f7852397896c4c431babafe21d655f376/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303232303932353130333433332e706e67)

### 2. Important details

- `fast` 要比 `slow` 快的相对速度为1



### 3. Complexity

- Time complexity: `O(n)`，快慢指针相遇前，指针走的次数小于链表长度，快慢指针相遇后，两个index指针走的次数也小于链表长度，总体为走的次数小于 `2n`
- Space complexity: `O(1)`



### 4. Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def detectCycle(self, head: Optional[ListNode]) -> Optional[ListNode]:
        fast = slow = head
        
        while fast and fast.next:
            fast = fast.next.next
            slow = slow.next
            # If there is a cycle, the slow and fast pointers will eventually meet
            if slow == fast:
                # Move one of the pointers back to the start of the list
                slow = head
                while slow != fast:
                    slow = slow.next
                    fast = fast.next
                return slow
        # If there is no cycle, return None
        return None
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
