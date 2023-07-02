# 203. Remove Linked List Elements

## Problem

*****

Given the `head` of a linked list and an integer `val`, remove all the nodes of the linked list that has `Node.val == val`, and return *the new head*.

 

**Example 1:**

![img](./0203%20Remove%20Linked%20List%20Elements.assets/removelinked-list.jpg)

```
Input: head = [1,2,6,3,4,5,6], val = 6
Output: [1,2,3,4,5]
```

**Example 2:**

```
Input: head = [], val = 1
Output: []
```

**Example 3:**

```
Input: head = [7,7,7,7], val = 7
Output: []
```

**Constraints:**

- The number of nodes in the list is in the range `[0, 104]`.
- `1 <= Node.val <= 50`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 dummy head 虚拟头节点法

### 1. Explanation

- 为了使对所有节点的处理一致，在head之前加一个虚拟头节点即可。

### 2. Important details

- 这一段记得是``if - else`

```python
            if current_node.next.val == val:
                current_node.next = current_node.next.next
            # 如果执行了上面那一行, 那么current_node.next 已经变了，所以需要再移动current_node
            else:
                current_node = current_node.next
```



### 3. Complexity

- Time complexity: ` O(N)`, 便利整个链表一次
- Space complexity:`O(1)`, it's a constant space solution.

### 4. Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        dummy_node = ListNode(0)
        dummy_node.next = head

        current_node = dummy_node
        while current_node.next != None:
            if current_node.next.val == val:
                current_node.next = current_node.next.next
            # 如果执行了上面那一行, 那么current_node.next 已经变了，所以需要再移动current_node
            else:
                current_node = current_node.next
        
        return dummy_node.next
```



********

## Solution2

### 1. Explanation

- 分两种情况
  - 一种是头节点值是`val`, 注意用`while`。
  - 另一种是非头节点值是`val`。

### 2. Important details

- 注意是`current_node.next.val` 不是只是 `current_node.next`, 总是在小细节上犯错。

```python
if current_node.next.val == val:
```

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
    def removeElements(self, head: Optional[ListNode], val: int) -> Optional[ListNode]:
        # 不使用虚拟头节点
        # 删除头节点，注意这里用while
        while head and head.val == val:
            head = head.next

        # 删除非头节点
        current_node = head
        while current_node and current_node.next:
            if current_node.next.val == val:
                current_node.next = current_node.next.next
            else:
                current_node = current_node.next
        
        return head
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
