# 404. Sum of Left Leaves

## Problem

*****

Given the `root` of a binary tree, return *the sum of all left leaves.*

A **leaf** is a node with no children. A **left leaf** is a leaf that is the left child of another node.

 

**Example 1:**

![img](./0404%20Sum%20of%20Left%20Leaves.assets/leftsum-tree.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: 24
Explanation: There are two left leaves in the binary tree, with values 9 and 15 respectively.
```

**Example 2:**

```
Input: root = [1]
Output: 0
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 1000]`.
- `-1000 <= Node.val <= 1000`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 后序遍历

### 1. Explanation

那么**判断当前节点是不是左叶子是无法判断的，必须要通过节点的父节点来判断其左孩子是不是左叶子。**

如果该节点的左节点不为空，该节点的左节点的左节点为空，该节点的左节点的右节点为空，则找到了一个左叶子，判断代码如下：

```cpp
if (node->left != NULL && node->left->left == NULL && node->left->right == NULL) {
    左叶子节点处理逻辑
}
```





### 2. Important details

- **平时我们解二叉树的题目时，已经习惯了通过节点的左右孩子判断本节点的属性，而本题我们要通过节点的父节点判断本节点的属性。**



### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: worst case `O(N)`



### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def sumOfLeftLeaves(self, root: Optional[TreeNode]) -> int:
        # Return case.
        if root is None:
            return 0
        if root.left is None and root.right is None:
            return 0
        # left right mid
        leftSumOfleftLeaves = self.sumOfLeftLeaves(root.left)
        # Find left leaf.
        leftValue = 0
        if root.left is not None and root.left.left is None and root.left.right is None:
            leftValue = root.left.val
        # 
        rightSumOfleftLeaves = self.sumOfLeftLeaves(root.right)
        # 
        sumOfLeftLeaves = leftValue + leftSumOfleftLeaves + rightSumOfleftLeaves
        return sumOfLeftLeaves
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
