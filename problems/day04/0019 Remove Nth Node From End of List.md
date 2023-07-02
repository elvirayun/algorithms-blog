# 19. Remove Nth Node From End of List

## Problem

*****

Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.

 

**Example 1:**

![img](./0019%20Remove%20Nth%20Node%20From%20End%20of%20List.assets/remove_ex1.jpg)

```
Input: head = [1,2,3,4,5], n = 2
Output: [1,2,3,5]
```

**Example 2:**

```
Input: head = [1], n = 1
Output: []
```

**Example 3:**

```
Input: head = [1,2], n = 1
Output: [1]
```

******

### 1. Classification



### 2. Discussion





*******

## Solution1 fast-slow pointers 快慢指针

### 1. Explanation

- `fast` 指针先走`n`步
- 然后`slow`和`fast`再同时走
- 当快指针到达最后一个节点时(因为要获得应被删除节点的前一个节点)，进行删除操作。

### 2. Important details



### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`



### 4. Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy_head = ListNode(next = head)
        slow = fast = dummy_head
    
        for i in range(n):
            fast = fast.next
        
        while fast.next:
            fast = fast.next
            slow = slow.next
        
        # slow points to the previous node of the node that should be deleted.
        slow.next = slow.next.next
        
        return dummy_head.next
```

********

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
