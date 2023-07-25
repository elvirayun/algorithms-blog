# 105. Construct Binary Tree from Preorder and Inorder Traversal

## Problem

*****

Given two integer arrays `preorder` and `inorder` where `preorder` is the preorder traversal of a binary tree and `inorder` is the inorder traversal of the same tree, construct and return *the binary tree*.

 

**Example 1:**

![img](./0105%20Construct%20Binary%20Tree%20from%20Preorder%20and%20Inorder%20Traversal%20%20%23%23%20.assets/tree-20230725032001360.jpg)

```
Input: preorder = [3,9,20,15,7], inorder = [9,3,15,20,7]
Output: [3,9,20,null,null,15,7]
```

**Example 2:**

```
Input: preorder = [-1], inorder = [-1]
Output: [-1]
```

 

**Constraints:**

- `1 <= preorder.length <= 3000`
- `inorder.length == preorder.length`
- `-3000 <= preorder[i], inorder[i] <= 3000`
- `preorder` and `inorder` consist of **unique** values.
- Each value of `inorder` also appears in `preorder`.
- `preorder` is **guaranteed** to be the preorder traversal of the tree.
- `inorder` is **guaranteed** to be the inorder traversal of the tree.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 同106 需要二刷



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
    def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
        # 第一步: 特殊情况讨论: 树为空. (递归终止条件)
        if not preorder:
            return None

        # 第二步: 后序遍历的最后一个就是当前的中间节点.
        root_val = preorder[0]
        root = TreeNode(root_val)

        # 第三步: 找切割点.
        separator_idx = inorder.index(root_val)

        # 第四步: 切割inorder数组. 得到inorder数组的左,右半边.
        inorder_left = inorder[:separator_idx]
        inorder_right = inorder[separator_idx + 1:]

        # 第五步: 切割postorder数组. 得到postorder数组的左,右半边.
        # ⭐️ 重点1: 中序数组大小一定跟后序数组大小是相同的.
        preorder_left = preorder[1:len(inorder_left) + 1]
        preorder_right = preorder[len(inorder_left) + 1: len(preorder) ]

        # 第六步: 递归
        root.left = self.buildTree(preorder_left, inorder_left )
        root.right = self.buildTree(preorder_right, inorder_right)
         # 第七步: 返回答案
        return root
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
