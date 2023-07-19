# 144. Binary Tree Preorder Traversal

## Problem

*****

Given the `root` of a binary tree, return *the preorder traversal of its nodes' values*.

 

**Example 1:**

![img](./0144%20Binary%20Tree%20Preorder%20Traversal.assets/inorder_1.jpg)

```
Input: root = [1,null,2,3]
Output: [1,2,3]
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

- The number of nodes in the tree is in the range `[0, 100]`.
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
        res.append(cur.val)
        self.traversal(cur.left, res)
        self.traversal(cur.right, res)
        
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
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
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if root == None:
            return []
        stack = []
        res = []
        stack.append(root)
        while stack:
            # Get current node
            cur = stack.pop()
            res.append(cur.val)
            # push right child node to stack.
            if cur.right:
                stack.append(cur.right)
            # then push left child node to stack.
            if cur.left:
                stack.append(cur.left)
        return res
```

## Solution3 统一迭代法 - 标记法

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
    # mid left right -> right left mid in stack
    def preorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        stack = []
        result = []
        if root:
            stack.append(root)
        while stack:
            cur_node = stack.pop()
            if cur_node:
                # right left mid.
                if cur_node.right:
                    stack.append(cur_node.right)
                if cur_node.left:
                    stack.append(cur_node.left)
                # Add a None node after mid None to tag it.
                stack.append(cur_node)
                stack.append(None)
            # Get None node. Save visited node to result.
            else:
                cur_node = stack.pop()
                result.append(cur_node.val)
        return result
```



## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
