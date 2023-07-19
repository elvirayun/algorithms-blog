# 145. Binary Tree Postorder Traversal

## Problem

*****

Given the `root` of a binary tree, return *the postorder traversal of its nodes' values*.

 

**Example 1:**

![img](./0145%20Binary%20Tree%20Postorder%20Traversal.assets/pre1.jpg)

```
Input: root = [1,null,2,3]
Output: [3,2,1]
```

**Example 2:**

```
Input: root = []
Output: []
```

**Example 3:**

```
Input: root = [1]
Output: [1]
```

 

**Constraints:**

- The number of the nodes in the tree is in the range `[0, 100]`.
- `-100 <= Node.val <= 100`

 

**Follow up:** Recursive solution is trivial, could you do it iteratively?

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归法

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
    def traversal(self, cur: Optional[TreeNode], res: list) -> None:
        if cur == None:
            return
        self.traversal(cur.left, res)
        self.traversal(cur.right, res)
        res.append(cur.val)

    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        self.traversal(root, res)
        return res
```



********

## Solution2 迭代法

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
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if root == None:
            return []
        stack = []
        res = []
        stack.append(root)
        while stack:
            cur = stack.pop()
            res.append(cur.val)
            # 中左右 -> 中右左
            if cur.left:
                stack.append(cur.left)
            if cur.right:
                stack.append(cur.right)
        return res[::-1]
```



## Solution3  标记法 - 统一迭代法

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
    def postorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        # left right mid -> mid right left in the stack.
        stack = []
        result = []
        if root:
            stack.append(root)
        while stack:
            cur_node = stack.pop()
            if cur_node:
                # Add None node.
                stack.append(cur_node)
                stack.append(None)
                # 
                if cur_node.right:
                    stack.append(cur_node.right)
                if cur_node.left:
                    stack.append(cur_node.left)
            else:
                cur_node = stack.pop()
                result.append(cur_node.val)
        return result
```



## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
