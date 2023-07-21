# 111. Minimum Depth of Binary Tree

## Problem

Given a binary tree, find its minimum depth.

The minimum depth is the number of nodes along the shortest path from the root node down to the nearest leaf node.

**Note:** A leaf is a node with no children.

 

**Example 1:**

![img](./0111%20Minimum%20Depth%20of%20Binary%20Tree.assets/ex_depth.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 2
```

**Example 2:**

```
Input: root = [2,null,3,null,4,null,5,null,6]
Output: 5
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[0, 105]`.
- `-1000 <= Node.val <= 1000`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

<img src="./0111%20Minimum%20Depth%20of%20Binary%20Tree.assets/111.%E4%BA%8C%E5%8F%89%E6%A0%91%E7%9A%84%E6%9C%80%E5%B0%8F%E6%B7%B1%E5%BA%A6.png" alt="111.二叉树的最小深度" style="zoom: 50%;" />

**求二叉树的最小深度和求二叉树的最大深度的差别主要在于处理左右孩子不为空的逻辑。**

### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python

```



********

## Solution2

### 1. Explanation





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
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        return self.getMinHeight(root)
    
    
    def getMinHeight(self, node: Optional[TreeNode]) -> int:
        if node == None:
            return 0

        leftMinHeight = self.getMinHeight(node.left)
        rightMinHeight = self.getMinHeight(node.right)
        # consider the case than only left or right tree is None.
        if node.left == None and node.right != None:
            minHeight = 1 + rightMinHeight
        elif node.left != None and node.right == None:
            minHeight = 1 + leftMinHeight
        else:
            minHeight = 1 + min(leftMinHeight, rightMinHeight)
        
        return minHeight
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
