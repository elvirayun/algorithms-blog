# 101. Symmetric Tree

## Problem

*****

Given the `root` of a binary tree, *check whether it is a mirror of itself* (i.e., symmetric around its center).

 

**Example 1:**

![img](./0101%20Symmetric%20Tree.assets/symtree1.jpg)

```
Input: root = [1,2,2,3,4,4,3]
Output: true
```

**Example 2:**

![img](./0101%20Symmetric%20Tree.assets/symtree2.jpg)

```
Input: root = [1,2,2,null,3,null,3]
Output: false
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 1000]`.
- `-100 <= Node.val <= 100`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation





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
    def compare(self, left: Optional[TreeNode], right: Optional[TreeNode]) -> Optional[TreeNode]:
        # 空节点的情况
        if left == None and right == None:
            return True
        elif left != None and right == None:
            return False
        elif left == None and right != None:
            return False
        # 值不相同的情况
        elif left.val != right.val:
            return False
        # 进入提供是值相同的情况
        outside = self.compare(left.left, right.right)
        inside = self.compare(left.right, right.left)
        isSame = outside and inside
        return isSame


    def isSymmetric(self, root: Optional[TreeNode]) -> bool:
        if not root:
            return True
        return self.compare(root.left, root.right)
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
