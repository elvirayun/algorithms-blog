# 559. Maximum Depth of N-ary Tree

## Problem

*****

Given a n-ary tree, find its maximum depth.

The maximum depth is the number of nodes along the longest path from the root node down to the farthest leaf node.

*Nary-Tree input serialization is represented in their level order traversal, each group of children is separated by the null value (See examples).*

 

**Example 1:**

![img](./0559%20Maximum%20Depth%20of%20N-ary%20Tree.assets/narytreeexample.png)

```
Input: root = [1,null,3,2,4,null,5,6]
Output: 3
```

**Example 2:**

![img](./0559%20Maximum%20Depth%20of%20N-ary%20Tree.assets/sample_4_964.png)

```
Input: root = [1,null,2,3,4,5,null,null,6,7,null,8,null,9,10,null,null,11,null,12,null,13,null,null,14]
Output: 5
```

 

**Constraints:**

- The total number of nodes is in the range `[0, 104]`.
- The depth of the n-ary tree is less than or equal to `1000`.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 二叉树 -> N叉树

### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def maxDepth(self, root: 'Node') -> int:
        return self.getHeight(root)
    

    def getHeight(self, node: Optional[TreeNode]) -> int:
        if not node:
            return 0
        height = 0
        for child in node.children:
            # Keep updating the height.
            height = max(height, self.getHeight(child))
        height = 1 + height
        return height
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
