# 669. Trim a Binary Search Tree

## Problem

*****

Given the `root` of a binary search tree and the lowest and highest boundaries as `low` and `high`, trim the tree so that all its elements lies in `[low, high]`. Trimming the tree should **not** change the relative structure of the elements that will remain in the tree (i.e., any node's descendant should remain a descendant). It can be proven that there is a **unique answer**.

Return *the root of the trimmed binary search tree*. Note that the root may change depending on the given bounds.

 

**Example 1:**

![img](./0669%20Trim%20a%20Binary%20Search%20Tree.assets/trim1.jpg)

```
Input: root = [1,0,2], low = 1, high = 2
Output: [1,null,2]
```

**Example 2:**

![img](./0669%20Trim%20a%20Binary%20Search%20Tree.assets/trim2.jpg)

```
Input: root = [3,0,4,null,2,null,null,1], low = 1, high = 3
Output: [3,2,null,1]
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 104]`.
- `0 <= Node.val <= 104`
- The value of each node in the tree is **unique**.
- `root` is guaranteed to be a valid binary search tree.
- `0 <= low <= high <= 104`

******

### 1. Classification



### 2. Discussion





*******

## Solution1  递归法

### 1. Explanation

- 牢记二叉搜索树有序的特性
- 关键点：将当前节点的子树返回给当前节点的父节点 -> 等于删除当前节点

### 2. Important details





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
    def trimBST(self, root: Optional[TreeNode], low: int, high: int) -> Optional[TreeNode]:
        # Return Case.
        if root is None:
            return None
        # 1. delete node here. BST
        if root.val < low:
            # 右子树可能有符合条件的节点
            right = self.trimBST(root.right, low, high)
            # 将当前节点的右子树返回给当前节点的父节点 -> 删除了当前节点
            return right
        if root.val > high:
            left = self.trimBST(root.left, low, high)
            return left
        # Recursion
        root.left = self.trimBST(root.left, low, high)
        root.right = self.trimBST(root.right, low, high)
        return root
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
