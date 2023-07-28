# 108. Convert Sorted Array to Binary Search Tree

## Problem

*****

Given an integer array `nums` where the elements are sorted in **ascending order**, convert *it to a* 

***height-balanced\***

 *binary search tree*.



 

**Example 1:**

![img](./0108%20Convert%20Sorted%20Array%20to%20Binary%20Search%20Tree.assets/btree1.jpg)

```
Input: nums = [-10,-3,0,5,9]
Output: [0,-3,9,-10,null,5]
Explanation: [0,-10,5,null,-3,null,9] is also accepted:
```

**Example 2:**

![img](./0108%20Convert%20Sorted%20Array%20to%20Binary%20Search%20Tree.assets/btree.jpg)

```
Input: nums = [1,3]
Output: [3,1]
Explanation: [1,null,3] and [3,1] are both height-balanced BSTs.
```

 

**Constraints:**

- `1 <= nums.length <= 104`
- `-104 <= nums[i] <= 104`
- `nums` is sorted in a **strictly increasing** order.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 自己写出来！！
- 关键点就是，利用二叉搜索树的有序特性
- 以及每次取中间节点进行创建二叉树节点来保证是平衡二叉搜索树
- 切割区间，默认左闭右开 [)



### 2. Important details

这段代码中并不会重复复制`nums`。虽然它在递归中传递了`nums`，但这并不意味着每次递归都会创建新的`nums`列表。在 Python 中，当你传递一个可变对象（如列表）到一个函数时，其实你传递的是该对象的引用，而不是对象本身。这意味着函数内部对该对象的修改会影响到原始对象。但是在这个代码中，并没有对`nums`进行修改，只是读取其某些元素，所以并不会复制`nums`。

然而，这个代码确实在每次递归调用时都创建了新的`TreeNode`，这是为了构建新的树节点。但这不是复制`nums`，而是创建新的树结构。 



### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def traversal(self, nums: List[int], left:int, right:int) -> Optional[TreeNode]:
        # left close and right open.
        # Return case.
        if left == right:
            return
        # Since the tree needs to be height-balanced, so we need to find mid
        mid = int( ( right - left ) / 2 ) + left
        root = TreeNode(nums[mid])
        root.left = self.traversal(nums, left, mid)
        root.right = self.traversal(nums, mid + 1, right)
        return root
        

    def sortedArrayToBST(self, nums: List[int]) -> Optional[TreeNode]:
        # find mid node as the current root.
        # mid index = ( right - left ) / 2 + left
        return self.traversal(nums, 0, len(nums)
```



********

## Solution2

### 1. Explanation





### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python

```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
