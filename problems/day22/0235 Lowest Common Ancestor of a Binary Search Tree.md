# 235. Lowest Common Ancestor of a Binary Search Tree

## Problem

*****

Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”

 

**Example 1:**

![img](./0235%20Lowest%20Common%20Ancestor%20of%20a%20Binary%20Search%20Tree.assets/binarysearchtree_improved.png)

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 8
Output: 6
Explanation: The LCA of nodes 2 and 8 is 6.
```

**Example 2:**

![img](./0235%20Lowest%20Common%20Ancestor%20of%20a%20Binary%20Search%20Tree.assets/binarysearchtree_improved.png)

```
Input: root = [6,2,8,0,4,7,9,null,null,3,5], p = 2, q = 4
Output: 2
Explanation: The LCA of nodes 2 and 4 is 2, since a node can be a descendant of itself according to the LCA definition.
```

**Example 3:**

```
Input: root = [2,1], p = 2, q = 1
Output: 2
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[2, 105]`.
- `-109 <= Node.val <= 109`
- All `Node.val` are **unique**.
- `p != q`
- `p` and `q` will exist in the BST.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归法

### 1. Explanation

- 代码随想录真的讲的好清晰！
- 关键就是二叉搜索树的特定，有序性
- 最后的情况囊括了其中有一个节点是父节点的情况，也就是 node.val == p.val 或者 node.val == q.val



### 2. Important details

- 从上往下遍历 遇到一个节点值在p和q中间，一定是最小公父节点。
- 



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
    # 递归法
    def traversal(self, node:'TreeNode', p:'TreeNode', q:'TreeNode') -> 'TreeNone':
        # 1. 返回条件
        if node is None:
            return None
        if node.val > p.val and node.val > q.val:
            left = self.traversal(node.left, p, q)
            if left:
                return left
        if node.val < p.val and node.val < q.val:
            right = self.traversal(node.right, p, q)
            if right:
                return right
        return node

    def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
        return self.traversal(root, p, q)
```



********

## Solution2 迭代法

### 1. Explanation





### 2. Important details

- TODO

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
        while root:
            if root.val > p.val and root.val > q.val:
                root = root.left
            # TODO：为什么这里是elif, if 不行？
            elif root.val < p.val and root.val < q.val:
                root = root.right
            else:
                return root
        return None
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
