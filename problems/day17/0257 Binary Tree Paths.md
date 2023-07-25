# 257. Binary Tree Paths

## Problem

*****

Given the `root` of a binary tree, return *all root-to-leaf paths in **any order***.

A **leaf** is a node with no children.

 

**Example 1:**

![img](./0257%20Binary%20Tree%20Paths.assets/paths-tree.jpg)

```
Input: root = [1,2,3,null,5]
Output: ["1->2->5","1->3"]
```

**Example 2:**

```
Input: root = [1]
Output: ["1"]
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[1, 100]`.
- `-100 <= Node.val <= 100`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归 ➕回溯

### 1. Explanation

- 递归➕回溯算法
- **所以回溯要和递归永远在一起，世界上最遥远的距离是你在花括号里，而我在花括号外！**

### 2. Important details

这段代码是在处理二叉树的节点遍历的问题。其主要功能是找到从根节点到所有叶子节点的所有路径，并且将这些路径以特定的格式储存在一个列表中。

其中的这一行代码 `sPath = '->'.join(map(str, path))` 执行的是如下操作：

1. `map(str, path)`: 这个 `map` 函数会对 `path` 列表中的每一个元素执行 `str` 函数，即将这些元素都转换为字符串。这里的 `path` 是一个存放节点值的列表，每次遍历到一个新的节点时，就将其值加入到这个列表中。当遍历到叶子节点时，`path` 中存放的就是从根节点到叶子节点的一条路径。

2. `'->'.join(...)`: 这个 `join` 函数会用指定的字符串 `'->'` 将 `map(str, path)` 的结果连接起来。这样，`sPath` 就变成了一条路径的字符串表示，路径中的各个节点之间用 `'->'` 连接。

举例来说，假如有一条路径是 `[1, 2, 3]`，那么 `sPath` 就会是 `'1->2->3'`。这个字符串会被添加到 `result` 列表中，最后 `result` 列表中的每一个元素都会是一条从根节点到叶子节点的路径的字符串表示。



### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`



### 4. Codes

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def binaryTreePaths(self, root: Optional[TreeNode]) -> List[str]:
        path = []
        result = []
        if not root:
            return result
        self.traversal(root, path, result)
        return result

    def traversal(self, curNode, path, result) -> None:
        # mid
        path.append(curNode.val)
        # return
        if curNode.left == None and curNode.right == None:
            pathStr = "->".join(map(str, path))
            result.append(pathStr)
            return
        # Make sure currNone.left != None
        if curNode.left:
            self.traversal(curNode.left, path, result)
            # 回溯
            path.pop()
        if curNode.right:
            self.traversal(curNode.right, path, result)
            path.pop()
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
