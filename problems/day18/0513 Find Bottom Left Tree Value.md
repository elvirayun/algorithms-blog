# 513. Find Bottom Left Tree Value

## Problem

*****

Given the `root` of a binary tree, return the leftmost value in the last row of the tree.

 

**Example 1:**

![img](./0513%20Find%20Bottom%20Left%20Tree%20Value.assets/tree1.jpg)

```
Input: root = [2,1,3]
Output: 1
```

**Example 2:**

![img](./0513%20Find%20Bottom%20Left%20Tree%20Value.assets/tree2.jpg)

```
Input: root = [1,2,3,4,null,5,6,null,null,7]
Output: 7
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 104]`.
- `-231 <= Node.val <= 231 - 1`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归 + 回溯法

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
    def findBottomLeftValue(self, root: Optional[TreeNode]) -> int:
        # 递归法 + 回溯
        self.maxDepth = float('-inf')
        self.result = None
        self.traversal(root, depth=0)
        return self.result
    

    def traversal(self, node, depth):
        if node.left is None and node.right is None:
            if depth > self.maxDepth:
                self.maxDepth = depth
                self.result = node.val
        if node.left:
            depth += 1
            self.traversal(node.left, depth)
            depth -= 1
        if node.right:
            depth += 1
            self.traversal(node.right, depth)
            depth -= 1
```



********

## Solution2 层序遍历

### 1. Explanation

- result 每次更新为最左边的节点即可



### 2. Important details

- `result = queue[i].val`: 还是要记得加.val



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
from collections import deque
class Solution:
    def findBottomLeftValue(self, root: Optional[TreeNode]) -> int:
        # Level traversal
        queue = deque()
        result = None
        if root is None:
            return 0
        queue.append(root)
        while queue:
            levelLength = len(queue)
            for i in range(levelLength):
                if i == 0:
                    result = queue[i].val
                cur_node = queue.popleft()
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
        return result
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
