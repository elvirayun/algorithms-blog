# 98. Validate Binary Search Tree

## Problem

*****

Given the `root` of a binary tree, *determine if it is a valid binary search tree (BST)*.

A **valid BST** is defined as follows:

- The left

   

  subtree

   

  of a node contains only nodes with keys

   

  less than

   

  the node's key.

- The right subtree of a node contains only nodes with keys **greater than** the node's key.

- Both the left and right subtrees must also be binary search trees.

 

**Example 1:**

![img](./0098%20Validate%20Binary%20Search%20Tree.assets/tree1-20230726003540728.jpg)

```
Input: root = [2,1,3]
Output: true
```

**Example 2:**

![img](./0098%20Validate%20Binary%20Search%20Tree.assets/tree2-20230726003540758.jpg)

```
Input: root = [5,1,4,null,null,3,6]
Output: false
Explanation: The root node's value is 5 but its right child's value is 4.
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 104]`.
- `-231 <= Node.val <= 231 - 1`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归 + list保存子树

### 1. Explanation

- 终于自己写对一题！
- 使用递归， 用list来保存左右子树
  - 那么list第一个数字就是子树的最小值
  - list的最后一个值就是子树的最大值




### 2. Important details

- 一些Python语法细节
  - not [] -> True
  - [] == False -> False
  - [] is None -> False




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
    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        print(self.recursion(root))
        return False if self.recursion(root) == False else True

    def recursion(self, root: Optional[TreeNode]) -> Optional[list]:
        # return case.
        if root is None:
            return []
        # minValue
        # maxValue
        # root.val > leftMax and root.val < rightMin
        # Use a node list
        # Make sure root.left and root.right are not None.
        leftValueList = self.recursion(root.left)
        if leftValueList == False: return False
        rightValueList = self.recursion(root.right)
        if rightValueList == False: return False
        # Check if BST
        # Ensure than left subtree and left subtree are BST.
        curValueList = [root.val]
        if len(leftValueList) != 0:
            if root.val > leftValueList[-1]:
                curValueList = leftValueList + curValueList
            else:
                return False
        if len(rightValueList) != 0:
            if root.val < rightValueList[0]:
                curValueList = curValueList + rightValueList
            else:
                return False
        return curValueList
```



********

## Solution2 递归法 + 利用二叉搜索树的中序遍历 + 双指针

### 1. Explanation

- 二叉树的中序遍历是递增的
- 所以可以用一个指针一直指向当前节点的前一个节点，来比较
- 如果一直是递增的话，说明就是二叉搜索树



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
# Inorder traversal - increasing list
# Use two pointers
class Solution:
    def __init__(self):
        self.pre = None  # 用来记录前一个节点

    def isValidBST(self, root: Optional[TreeNode]) -> bool:
        if root is None:
            return True
        # Inorder traversal
        left = self.isValidBST(root.left)
        if self.pre != None and self.pre.val >= root.val:
            return False
        self.pre = root
        right = self.isValidBST(root.right)
        return left and right
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
