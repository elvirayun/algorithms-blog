# 222. Count Complete Tree Nodes

## Problem

*****

Given the `root` of a **complete** binary tree, return the number of the nodes in the tree.

According to **[Wikipedia](http://en.wikipedia.org/wiki/Binary_tree#Types_of_binary_trees)**, every level, except possibly the last, is completely filled in a complete binary tree, and all nodes in the last level are as far left as possible. It can have between `1` and `2h` nodes inclusive at the last level `h`.

Design an algorithm that runs in less than `O(n)` time complexity.

 

**Example 1:**

![img](./0222%20Count%20Complete%20Tree%20Nodes.assets/complete.jpg)

```
Input: root = [1,2,3,4,5,6]
Output: 6
```

**Example 2:**

```
Input: root = []
Output: 0
```

**Example 3:**

```
Input: root = [1]
Output: 1
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[0, 5 * 104]`.
- `0 <= Node.val <= 5 * 104`
- The tree is guaranteed to be **complete**.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

<img src="./0222%20Count%20Complete%20Tree%20Nodes.assets/20200920221638903-20230310123444151.png" alt="img" style="zoom: 50%;" />

<img src="./0222%20Count%20Complete%20Tree%20Nodes.assets/20201124092543662.png" alt="222.完全二叉树的节点个数" style="zoom:50%;" />

<img src="./0222%20Count%20Complete%20Tree%20Nodes.assets/20220829163554.png" alt="img" style="zoom:50%;" />

### 2. Important details

- `return ( 2 << leftNodesNum ) - 1`  中 `2 << leftNodesNum ` 要加括号
- 注意(2<<1) 相当于2^2，返回满足满二叉树的子树节点数量， 所以在判断是否为满二叉子树时，leftNodesNum是从0开始。



### 3. Complexity

TODO: 复杂度分析

- Time complexity:
- Space complexity:



### 4. Code

- 利用完全二叉树的特性

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        return self.getNodesNum(root)
    
    def getNodesNum(self, node: Optional[TreeNode]) -> int:
        # 两种情况：空节点和是满二叉树
        if node == None:
            return 0
        # 满二叉树
        left, right = node.left, node.right
        leftNodesNum, rightNodesNum = 0, 0
        while left:
            left = left.left
            leftNodesNum += 1
        while right:
            right = right.right
            rightNodesNum += 1
        if leftNodesNum == rightNodesNum:
            # 注意(2<<1) 相当于2^2，返回满足满二叉树的子树节点数量
            return ( 2 << leftNodesNum ) - 1
        # 单层递归逻辑
        leftNodesNum = self.getNodesNum(node.left)
        rightNodesNum = self.getNodesNum(node.right)
        curNodesNum = leftNodesNum + rightNodesNum + 1
        return curNodesNum
```

- 当作普通二叉树解法

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def countNodes(self, root: Optional[TreeNode]) -> int:
        return self.getNodesNum(root)
    
    def getNodesNum(self, node: Optional[TreeNode]) -> int:
        if node == None:
            return 0
        leftNodesNum = self.getNodesNum(node.left)
        rightNodesNum = self.getNodesNum(node.right)
        curNodesNum = 1 + leftNodesNum + rightNodesNum
        return curNodesNum
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
