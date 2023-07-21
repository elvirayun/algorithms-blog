# 226. Invert Binary Tree

## Problem

*****

Given the `root` of a binary tree, invert the tree, and return *its root*.

 

**Example 1:**

![img](./0226%20Invert%20Binary%20Tree.assets/invert1-tree.jpg)

```
Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]
```

**Example 2:**

![img](./0226%20Invert%20Binary%20Tree.assets/invert2-tree.jpg)

```
Input: root = [2,1,3]
Output: [2,3,1]
```

**Example 3:**

```
Input: root = []
Output: []
```

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归法

### 1. Explanation





### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:

**Complexity Analysis**

Since each node in the tree is visited only once, the time complexity is O(n), where nn*n* is the number of nodes in the tree. We cannot do better than that, since at the very least we have to visit each node to invert it.

时间复杂度：每个节点访问一次。

Because of recursion, O(h) function calls will be placed on the stack in the worst case, where hh*h* is the height of the tree. Because h∈O(n), the space complexity is O(n)。

最坏情况下 h == n, 二叉树退化成链表

### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return None
        # swap root.left and root.right
        # preorder
        root.left, root.right = root.right, root.left
        self.invertTree(root.left)
        self.invertTree(root.right)
        return root
```



```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return None
        # swap root.left and root.right
        # post order.
        self.invertTree(root.left)
        self.invertTree(root.right)
        root.left, root.right = root.right, root.left
        return root
```



```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root:
            return None
        # swap root.left and root.right
        # in order.
        self.invertTree(root.left)
        root.left, root.right = root.right, root.left
        # As unreversed right tree became left tree.
        self.invertTree(root.left)
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
- [Leetcode.com](

- 