# 94. Binary Tree Inorder Traversal

## Problem

*****

Given the `root` of a binary tree, return *the inorder traversal of its nodes' values*.

 

**Example 1:**

![img](./0094%20Binary%20Tree%20Inorder%20Traversal.assets/inorder_1-20230719105546347.jpg)

```
Input: root = [1,null,2,3]
Output: [1,3,2]
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

- 递归即可

### 2. Important details



### 3. Complexity

TODO:

- Time complexity: O(n)

  The time complexity is O(n) because the recursive function is T(n)=2⋅T(n/2)+1

- Space complexity: O(n)

  - The worst case space required is O(n), and in the average case it's O(log⁡n) where nn*n* is number of nodes.



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
        res.append(cur.val)
        self.traversal(cur.right, res)

    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        res = []
        self.traversal(root, res)
        return res
```



********

## Solution2 迭代法

### 1. Explanation

- 和前序和后序遍历不同

### 2. Important details





### 3. Complexity

- Time complexity: O(N)
- Space complexity: O(N)



### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        if root == None:
            return []
        # 后序遍历不把root先放进去
        stack = []
        result = []
        cur = root
        while cur or stack:
            # 先一路向左，把遍历过的节点存入stack
            if cur:
                stack.append(cur)
                cur = cur.left
            # cur == None, 说明以到达最左下角
            else:
                cur = stack.pop()
                # 存入result数组, 此时存入的是中
                # 记得result数组是int型，只存value
                result.append(cur.val)
                # 查看cur的右孩子
                cur = cur.right
        return result

# Time: O(N), n是节点数
# Space: O(N), stack的存储空间
                
```

## Solution2 标记法 - 统一迭代法

### 1. Explanation

- 用空节点标记已经访问过的节点

### 2. Important details



### 3. Complexity

- Time complexity: O(N)

- Space complexity: O(N)

  

### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    # 中序遍历 左中右
    def inorderTraversal(self, root: Optional[TreeNode]) -> List[int]:
        # stack 用于遍历访问, result存返回的结果
        stack = []
        result = []
        if root: 
            stack.append(root)
        while stack:
            # 如果当前节点不为None, 就从栈中弹出访问
            cur_node = stack.pop()
            if cur_node:
                # 
                if cur_node.right: 
                    stack.append(cur_node.right)
                # 用一个None节点标记访问过的节点
                stack.append(cur_node)
                stack.append(None)
                # 
                if cur_node.left:
                    stack.append(cur_node.left)
            # 如果访问到None，说明遇到了访问过的节点，存入result数组
            else:
                cur_node = stack.pop()
                result.append(cur_node.val)
        return result
```



## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
