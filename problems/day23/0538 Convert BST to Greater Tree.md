# 538. Convert BST to Greater Tree

## Problem

*****

Given the `root` of a Binary Search Tree (BST), convert it to a Greater Tree such that every key of the original BST is changed to the original key plus the sum of all keys greater than the original key in BST.

As a reminder, a *binary search tree* is a tree that satisfies these constraints:

- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.

 

**Example 1:**

![img](./0538%20Convert%20BST%20to%20Greater%20Tree.assets/tree.png)

```
Input: root = [4,1,6,0,2,5,7,null,null,null,3,null,null,null,8]
Output: [30,36,21,36,35,26,15,null,null,null,33,null,null,null,8]
```

**Example 2:**

```
Input: root = [0,null,1]
Output: [1,null,1]
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[0, 104]`.
- `-104 <= Node.val <= 104`
- All the values in the tree are **unique**.
- `root` is guaranteed to be a valid binary search tree.

 

**Note:** This question is the same as 1038: https://leetcode.com/problems/binary-search-tree-to-greater-sum-tree/

******

### 1. Classification



### 2. Discussion





*******

## Solution1递归法 - 简洁解决-pre指向树值

### 1. Explanation

- 和1038题相同

- 用pre指针指向前一个节点即可（或者直接代表数值即可，数值更加简介）
- 二叉搜索从大到小：右中左



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
    def __init__(self) -> None:
        # pre指向前一个节点的树值
        self.preValue = 0

    def traversal(self, node: Optional[TreeNode]) -> Optional[TreeNode]:
        # right mid left
        # Return Case
        if node is None:
            return
        # right
        node.right = self.traversal(node.right)
        node.val += self.preValue
        # update pre
        self.preValue = node.val
        node.left = self.traversal(node.left)
        return node 

    def convertBST(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        return self.traversal(root)
```



********

## Solution2 自己解法 - 递归 - pre指向节点

### 1. Explanation

- 又自己做出来！！
- pre指向节点
- 指向节点要注意：遇到第一个节点要初始化pre并且不自己➕自己第一个



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
    def __init__(self) -> None:
        self.pre = None

    def traversal(self, node: Optional[TreeNode]) -> Optional[TreeNode]:
        # right mid left
        # Return Case
        if node is None:
            return
        # right
        node.right = self.traversal(node.right)
        # Inital pre node 并且第一个节点不操作
        if self.pre is None:
            self.pre = node
        # 这里操作节点
        else:
            node.val += self.pre.val
            # update pre
            self.pre = node
        node.left = self.traversal(node.left)
        return node 

    def convertBST(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        return self.traversal(root)
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
