# 700. Search in a Binary Search Tree

## Problem

*****

You are given the `root` of a binary search tree (BST) and an integer `val`.

Find the node in the BST that the node's value equals `val` and return the subtree rooted with that node. If such a node does not exist, return `null`.

 

**Example 1:**

![img](./0700%20Search%20in%20a%20Binary%20Search%20Tree.assets/tree1-20230725222526343.jpg)

```
Input: root = [4,2,7,1,3], val = 2
Output: [2,1,3]
```

**Example 2:**

![img](./0700%20Search%20in%20a%20Binary%20Search%20Tree.assets/tree2-20230725222526347.jpg)

```
Input: root = [4,2,7,1,3], val = 5
Output: []
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 5000]`.
- `1 <= Node.val <= 107`
- `root` is a binary search tree.
- `1 <= val <= 107`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归遍历法

### 1. Explanation

- 充分利用二叉搜索树的特性
  - root.left 的所有值都小于root.val
  - root.right 的所有值都大于root.val
  - 所有子树也遵循这个规则
  - 大小顺序：左中右

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
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        # Recursion traversal
        if root is None or root.val == val:
            return root
        # Recursion logic - single level.
        if val > root.val:
            result = self.searchBST(root.right, val)
        if val < root.val:
            result = self.searchBST(root.left, val)
        return result
```



********

## Solution2 迭代法

### 1. Explanation

- 很简单的迭代法！

### 2. Important details

- TODO：TC 和 SC



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
    def searchBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        # 迭代法
        while root:
            if root.val == val:
                return root
            elif root.val > val:
                root = root.left
            else:
                root = root.right
        return None    
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
