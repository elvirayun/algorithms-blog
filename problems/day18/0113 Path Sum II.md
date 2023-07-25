# 113. Path Sum II

## Problem

*****

Given the `root` of a binary tree and an integer `targetSum`, return *all **root-to-leaf**paths where the sum of the node values in the path equals* `targetSum`*. Each path should be returned as a list of the node **values**, not node references*.

A **root-to-leaf** path is a path starting from the root and ending at any leaf node. A **leaf**is a node with no children.

 

**Example 1:**

![img](./0113%20Path%20Sum%20II.assets/pathsumii1.jpg)

```
Input: root = [5,4,8,11,null,13,4,7,2,null,null,5,1], targetSum = 22
Output: [[5,4,11,2],[5,8,4,5]]
Explanation: There are two paths whose sum equals targetSum:
5 + 4 + 11 + 2 = 22
5 + 8 + 4 + 5 = 22
```

**Example 2:**

![img](./0113%20Path%20Sum%20II.assets/pathsum2-20230725024112514.jpg)

```
Input: root = [1,2,3], targetSum = 5
Output: []
```

**Example 3:**

```
Input: root = [1,2], targetSum = 0
Output: []
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[0, 5000]`.
- `-1000 <= Node.val <= 1000`
- `-1000 <= targetSum <= 1000`

******

### 1. Classification



### 2. Discussion





*******

## Solution1递归➕回溯

### 1. Explanation

- 和112题类似



### 2. Important details

- 为什么 self.result.append(self.path[:]) 和 self.result.append(self.path) 结果不一样

这两行代码之间的主要区别在于它们处理对象引用的方式。Python 中的列表是可变的，这意味着你可以改变一个列表的内容而不改变它在内存中的位置。当你使用 `self.result.append(self.path)` 时，你实际上是将 `self.path` 列表的引用添加到 `self.result` 中。这意味着如果在后续的代码中更改了 `self.path` 的内容，那么这个改变也会反映在 `self.result` 中，因为它们都指向同一个列表。

然而，如果你使用 `self.result.append(self.path[:])`，你则是创建了 `self.path` 的一个副本，并将这个副本添加到了 `self.result` 中。这样，即使 `self.path` 的内容在后续被更改，`self.result` 中的对应列表不会发生变化，因为它保存的是 `self.path` 在添加时的状态。

总结起来，如果你希望 `self.result` 中保存 `self.path` 的当前状态并且不希望后续的更改影响它，你应该使用 `self.result.append(self.path[:])`。如果你希望 `self.result` 中的列表能反映 `self.path` 的最新状态，你应该使用 `self.result.append(self.path)`。

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
    def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
        self.path = []
        self.result = []
        if root is None:
            return []
        self.path.append(root.val)
        self.traversal(root, targetSum - root.val)
        return self.result

    def traversal(self, node: Optional[TreeNode], count: int):
        # return case.
        if node.left is None and node.right is None:
            if count == 0:
                self.result.append(self.path[:])
            return
        # left
        if node.left:
            self.path.append(node.left.val)
            self.traversal(node.left, count - node.left.val)
            self.path.pop()
        # right
        if node.right:
            self.path.append(node.right.val)
            self.traversal(node.right, count - node.right.val)
            self.path.pop()
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
