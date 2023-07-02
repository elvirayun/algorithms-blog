# 160. Intersection of Two Linked Lists

## Problem

*****

Given the heads of two singly linked-lists `headA` and `headB`, return *the node at which the two lists intersect*. If the two linked lists have no intersection at all, return `null`.

For example, the following two linked lists begin to intersect at node `c1`:

![img](./0160%20Intersection%20of%20Two%20Linked%20Lists.assets/160_statement.png)

The test cases are generated such that there are no cycles anywhere in the entire linked structure.

**Note** that the linked lists must **retain their original structure** after the function returns.

**Custom Judge:**

The inputs to the **judge** are given as follows (your program is **not** given these inputs):

- `intersectVal` - The value of the node where the intersection occurs. This is `0` if there is no intersected node.
- `listA` - The first linked list.
- `listB` - The second linked list.
- `skipA` - The number of nodes to skip ahead in `listA` (starting from the head) to get to the intersected node.
- `skipB` - The number of nodes to skip ahead in `listB` (starting from the head) to get to the intersected node.

The judge will then create the linked structure based on these inputs and pass the two heads, `headA` and `headB` to your program. If you correctly return the intersected node, then your solution will be **accepted**.

 

**Example 1:**

![img](./0160%20Intersection%20of%20Two%20Linked%20Lists.assets/160_example_1_1.png)

```
Input: intersectVal = 8, listA = [4,1,8,4,5], listB = [5,6,1,8,4,5], skipA = 2, skipB = 3
Output: Intersected at '8'
Explanation: The intersected node's value is 8 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [4,1,8,4,5]. From the head of B, it reads as [5,6,1,8,4,5]. There are 2 nodes before the intersected node in A; There are 3 nodes before the intersected node in B.
- Note that the intersected node's value is not 1 because the nodes with value 1 in A and B (2nd node in A and 3rd node in B) are different node references. In other words, they point to two different locations in memory, while the nodes with value 8 in A and B (3rd node in A and 4th node in B) point to the same location in memory.
```

**Example 2:**

![img](./0160%20Intersection%20of%20Two%20Linked%20Lists.assets/160_example_2.png)

```
Input: intersectVal = 2, listA = [1,9,1,2,4], listB = [3,2,4], skipA = 3, skipB = 1
Output: Intersected at '2'
Explanation: The intersected node's value is 2 (note that this must not be 0 if the two lists intersect).
From the head of A, it reads as [1,9,1,2,4]. From the head of B, it reads as [3,2,4]. There are 3 nodes before the intersected node in A; There are 1 node before the intersected node in B.
```

**Example 3:**

![img](./0160%20Intersection%20of%20Two%20Linked%20Lists.assets/160_example_3.png)

```
Input: intersectVal = 0, listA = [2,6,4], listB = [1,5], skipA = 3, skipB = 2
Output: No intersection
Explanation: From the head of A, it reads as [2,6,4]. From the head of B, it reads as [1,5]. Since the two lists do not intersect, intersectVal must be 0, while skipA and skipB can be arbitrary values.
Explanation: The two lists do not intersect, so return null.
```

 

**Constraints:**

- The number of nodes of `listA` is in the `m`.
- The number of nodes of `listB` is in the `n`.
- `1 <= m, n <= 3 * 104`
- `1 <= Node.val <= 105`
- `0 <= skipA < m`
- `0 <= skipB < n`
- `intersectVal` is `0` if `listA` and `listB` do not intersect.
- `intersectVal == listA[skipA] == listB[skipB]` if `listA` and `listB` intersect.

 

**Follow up:** Could you write a solution that runs in `O(m + n)` time and use only `O(1)`memory?

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- [题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/面试题02.07.链表相交.md#其他语言版本)

<img src="https://camo.githubusercontent.com/6429ecba1867684dee684af4833926c0468683ead1e0fb189bf6ee0fbf71381e/68747470733a2f2f636f64652d7468696e6b696e672e63646e2e626365626f732e636f6d2f706963732f25453925394425413225453825414625393525453925413225393830322e30372e2545392539332542452545382541312541382545372539422542382545342542412541345f322e706e67" alt="面试题02.07.链表相交_2" style="zoom:50%;" />

- 因为从相交开始后面的部分一定长度相同
- 所以如图所示，先让长链表的指针指向和短链表头指针相等的位置
- 再同时移动headA和headB 找到相交指针。

### 2. Important details





### 3. Complexity

- Time complexity: `O(N+M)`, 两条链表都走了两遍
- Space complexity: `O(1)`



### 4. Code

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getIntersectionNode(self, headA: ListNode, headB: ListNode) -> Optional[ListNode]:
        lenA = self.get_length(headA)
        lenB = self.get_length(headB)

        if lenA > lenB:
            headA = self.move_forward(headA, lenA - lenB)
        else:
            headB = self.move_forward(headB, lenB - lenA)

        while headA:
            if headA == headB:
                return headA
            headA = headA.next
            headB = headB.next
            
        return None


    def get_length(self, head: ListNode) -> int:
        length = 0
        while head:
            length += 1
            head = head.next
        return length


    def move_forward(self, head: ListNode, steps: int) -> ListNode:
        for i in range(steps):
            head = head.next
        return head
```



## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
