# 104. Maximum Depth of Binary Tree

## Problem

*****

Given the `root` of a binary tree, return *its maximum depth*.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.

 

**Example 1:**

![img](./0104%20Maximum%20Depth%20of%20Binary%20Tree.assets/tmp-tree.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 3
```

**Example 2:**

```
Input: root = [1,null,2]
Output: 2
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[0, 104]`.
- `-100 <= Node.val <= 100`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归法

### 1. Explanation

- 后序遍历

<img src="./0104%20Maximum%20Depth%20of%20Binary%20Tree.assets/image-20230721103504195.png" alt="image-20230721103504195" style="zoom: 25%;" />

### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity:



### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
# 递归法 -- 后序遍历
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        return self.getHeight(root)
    

    def getHeight(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        leftHeight = self.getHeight(root.left) # 左
        rightHeight = self.getHeight(root.right) # 右
        height = 1 + max(leftHeight, rightHeight) # 中
        return height
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
