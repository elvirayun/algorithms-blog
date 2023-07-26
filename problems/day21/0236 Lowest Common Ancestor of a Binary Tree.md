# 236. Lowest Common Ancestor of a Binary Tree

## Problem

*****

Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T`that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”

 

**Example 1:**

![img](./0236%20Lowest%20Common%20Ancestor%20of%20a%20Binary%20Tree.assets/binarytree.png)

```
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 1
Output: 3
Explanation: The LCA of nodes 5 and 1 is 3.
```

**Example 2:**

![img](./0236%20Lowest%20Common%20Ancestor%20of%20a%20Binary%20Tree.assets/binarytree.png)

```
Input: root = [3,5,1,6,2,0,8,null,null,7,4], p = 5, q = 4
Output: 5
Explanation: The LCA of nodes 5 and 4 is 5, since a node can be a descendant of itself according to the LCA definition.
```

**Example 3:**

```
Input: root = [1,2], p = 1, q = 2
Output: 1
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[2, 105]`.
- `-109 <= Node.val <= 109`
- All `Node.val` are **unique**.
- `p != q`
- `p` and `q` will exist in the tree.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- TODO： 需要二刷

![236.二叉树的最近公共祖先2](./0236%20Lowest%20Common%20Ancestor%20of%20a%20Binary%20Tree.assets/202102041512582.png)



### 2. Important details

if root == p or root == q: 包含了两种情况

- 公共祖先是两个节点的根节点

- 公共祖先是两个节点之一

  



### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        if root is None:
            return None
        if root == p or root == q:
            return root
        # 后序遍历
        # 左
        left = self.lowestCommonAncestor(root.left, p, q)
        # 右
        right = self.lowestCommonAncestor(root.right, p, q)
        # 中
        # Find common ancestor
        if left and right:
            return root
        if left:
            return left
        if right:
            return right
        return None
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
