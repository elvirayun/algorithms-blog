# 701. Insert into a Binary Search Tree

## Problem

*****

ou are given the `root` node of a binary search tree (BST) and a `value` to insert into the tree. Return *the root node of the BST after the insertion*. It is **guaranteed** that the new value does not exist in the original BST.

**Notice** that there may exist multiple valid ways for the insertion, as long as the tree remains a BST after insertion. You can return **any of them**.

 

**Example 1:**

![img](./0701%20Insert%20into%20a%20Binary%20Search%20Tree.assets/insertbst.jpg)

```
Input: root = [4,2,7,1,3], val = 5
Output: [4,2,7,1,3,5]
Explanation: Another accepted tree is:
```

**Example 2:**

```
Input: root = [40,20,60,10,30,50,70], val = 25
Output: [40,20,60,10,30,50,70,null,null,25]
```

**Example 3:**

```
Input: root = [4,2,7,1,3,null,null,null,null,null,null], val = 5
Output: [4,2,7,1,3,5]
```

 

**Constraints:**

- The number of nodes in the tree will be in the range `[0, 104]`.
- `-108 <= Node.val <= 108`
- All the values `Node.val` are **unique**.
- `-108 <= val <= 108`
- It's **guaranteed** that `val` does not exist in the original BST.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归法

### 1. Explanation

- 在二叉搜索树插入节点时只需要在二叉搜索树的叶子节点插入即可
- 递归法很简洁

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
    def insertIntoBST(self, root: Optional[TreeNode], val: int) -> Optional[TreeNode]:
        # 为None时说明找到了插入的位置                                                   
        if root is None:
            newNode = TreeNode(val)
            return newNode
        # 往左走
        if root.val > val:
            root.left = self.insertIntoBST(root.left, val)
        # 往右走
        if root.val < val:
            root.right = self.insertIntoBST(root.right, val)
        return root
```



********

## Solution2

### 1. Explanation

- TODO: 学习迭代法

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
