# 501. Find Mode in Binary Search Tree

## Problem

*****

Given the `root` of a binary search tree (BST) with duplicates, return *all the [mode(s)](https://en.wikipedia.org/wiki/Mode_(statistics)) (i.e., the most frequently occurred element) in it*.

If the tree has more than one mode, return them in **any order**.

Assume a BST is defined as follows:

- The left subtree of a node contains only nodes with keys **less than or equal to** the node's key.
- The right subtree of a node contains only nodes with keys **greater than or equal to** the node's key.
- Both the left and right subtrees must also be binary search trees.

 

**Example 1:**

![img](./0501%20Find%20Mode%20in%20Binary%20Search%20Tree.assets/mode-tree.jpg)

```
Input: root = [1,null,2,2]
Output: [2]
```

**Example 2:**

```
Input: root = [0]
Output: [0]
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 104]`.
- `-105 <= Node.val <= 105`

 

**Follow up:** Could you do that without using any extra space? (Assume that the implicit stack space incurred due to recursion does not count).

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 中序遍历
- 双指针法
- 动态更新result数组



### 2. Important details

- 记得更新pre节点！



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
        self.result = []
        self.count = 0
        self.maxCount = 0
        self.pre = None
        
    def findMode(self, root: Optional[TreeNode]) -> List[int]:
        # 终止条件
        if root is None:
            return
        # 左
        self.findMode(root.left)
        # 中
        if self.pre == None:            # 第一个节点
            self.count = 1 
        elif self.pre.val == root.val:  #相同节点
            self.count += 1
        else:                           # 遇到新节点
            self.count = 1
        self.pre = root                 # 需要更新上一个节点
        # 
        if self.count == self.maxCount:
            self.result.append(root.val)
        if self.count > self.maxCount:
            self.maxCount = self.count
            self.result = [root.val]
        # 右
        self.findMode(root.right)
        return self.result
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
