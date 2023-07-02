# 206. Reverse Linked List

## Problem

*****

Given the `head` of a singly linked list, reverse the list, and return *the reversed list*.

 

**Example 1:**

![img](./0206%20Reverse%20Linked%20List.assets/rev1ex1.jpg)

```
Input: head = [1,2,3,4,5]
Output: [5,4,3,2,1]
```

**Example 2:**

![img](./0206%20Reverse%20Linked%20List.assets/rev1ex2.jpg)

```
Input: head = [1,2]
Output: [2,1]
```

**Example 3:**

```
Input: head = []
Output: []
```

 

**Constraints:**

- The number of nodes in the list is the range `[0, 5000]`.
- `-5000 <= Node.val <= 5000`

 

**Follow up:** A linked list can be reversed either iteratively or recursively. Could you implement both?

******

### 1. Classification



### 2. Discussion





*******

## Solution1 Two pionters

### 1. Explanation

- 这个解法很清晰！

- 首先定义一个cur指针，指向头结点，再定义一个pre指针，初始化为null。

  然后就要开始反转了，首先要把 cur->next 节点用tmp指针保存一下，也就是保存一下这个节点。

  为什么要保存一下这个节点呢，因为接下来要改变 cur->next 的指向了，将cur->next 指向pre ，此时已经反转了第一个节点了。

  接下来，就是循环走如下代码逻辑了，继续移动pre和cur指针。

  最后，cur 指针已经指向了null，循环结束，链表也反转完毕了。 此时我们return pre指针就可以了，pre指针就指向了新的头结点。

- [解法网址](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0206.翻转链表.md#思路)

<img src="./0206%20Reverse%20Linked%20List.assets/image-20230702005246110.png" alt="image-20230702005246110" style="zoom: 33%;" />

### 2. Important details





### 3. Complexity

- Time complexity: ` O(n)`
- Space complexity: `O(1)`



### 4. Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        # Two pointers
        pre = None
        cur = head
        while cur != None:
            temp = cur.next
            cur.next = pre
            pre = cur
            cur = temp
        return pre
```



********

## Solution2 递归法

### 1. Explanation

- 对照着双指针写法写递归函数
- 递归写法需要复习

### 2. Important details

- 记得在递归函数里是需要 return 自己

  ```python
  return self.reverse(cur, temp)
  ```


### 3. Complexity

- Time complexity: `O(N)`, 要递归处理链表的每个节点

- Space complexity: `O(N)`, 递归调用了 n 层栈空间

  

### 4. Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
    def reverse(self, pre: Optional[ListNode], cur: Optional[ListNode]) -> Optional[ListNode]:
        if cur == None: 
            return pre
        temp = cur.next
        cur.next = pre
        return self.reverse(cur, temp)
       
    def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        return self.reverse(None, head)
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
