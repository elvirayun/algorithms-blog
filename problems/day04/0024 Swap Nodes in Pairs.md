# 24. Swap Nodes in Pairs

## Problem

*****

Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)

 

**Example 1:**

![img](./0024%20Swap%20Nodes%20in%20Pairs.assets/swap_ex1-20230702022007753.jpg)

```
Input: head = [1,2,3,4]
Output: [2,1,4,3]
```

**Example 2:**

```
Input: head = []
Output: []
```

**Example 3:**

```
Input: head = [1]
Output: [1]
```

 

**Constraints:**

- The number of nodes in the list is in the range `[0, 100]`.
- `0 <= Node.val <= 100`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

<img src="./0024%20Swap%20Nodes%20in%20Pairs.assets/image-20230702022732155.png" alt="image-20230702022732155" style="zoom:50%;" />

![image-20230702022748174](./0024%20Swap%20Nodes%20in%20Pairs.assets/image-20230702022748174.png)

<img src="./0024%20Swap%20Nodes%20in%20Pairs.assets/image-20230702022933583.png" alt="image-20230702022933583" style="zoom:50%;" />



### 2. Important details

- 当节点数为偶数时，current.next == None 为中止条件；当节点数为奇数时, current.next.next == None为中止条件。

```python
while current.next and current.next.next:
```

- 记得保存第一个节点和第三个节点。

- ```python
  temp_third = current.next.next.next
  ```

- 操作某一个节点一定要找到它的前一个节点。

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
    def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
        dummy_head = ListNode(next=head)
        current = dummy_head
        
        while current.next and current.next.next:
            # save the first node and the third node.
            temp_first = current.next
            temp_third = current.next.next.next

            # start swap.
            # current -> second
            current.next = current.next.next
            # second -> first
            current.next.next = temp_first
            # first -> third
            temp_first.next = temp_third

            # update current
            current = current.next.next

        return dummy_head.next
```



********

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
