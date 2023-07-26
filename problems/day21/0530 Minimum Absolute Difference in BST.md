# 530. Minimum Absolute Difference in BST

## Problem

*****

Given the `root` of a Binary Search Tree (BST), return *the minimum absolute difference between the values of any two different nodes in the tree*.

 

**Example 1:**

![img](./0530%20Minimum%20Absolute%20Difference%20in%20BST.assets/bst1.jpg)

```
Input: root = [4,2,6,1,3]
Output: 1
```

**Example 2:**

![img](./0530%20Minimum%20Absolute%20Difference%20in%20BST.assets/bst2.jpg)

```
Input: root = [1,0,48,null,null,12,49]
Output: 1
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[2, 104]`.
- `0 <= Node.val <= 105`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归 中序遍历 双指针

### 1. Explanation

- 和Validate Binary Search Tree 类似
- 都是利用BST的中序遍历是递增数组的特性
- 使用一个指针记录前一个节点
- 和783题相同

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
        self.minDiff = float('inf')
        self.pre = None

    def getMinimumDifference(self, root: Optional[TreeNode]) -> int:
        if root is None:
            return
        self.getMinimumDifference(root.left)
        if self.pre != None:
            self.minDiff = min(self.minDiff, root.val - self.pre.val)
        self.pre = root
        self.getMinimumDifference(root.right)
        return self.minDiff 
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
