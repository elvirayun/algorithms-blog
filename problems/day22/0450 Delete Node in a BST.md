# 450. Delete Node in a BST

## Problem

*****

Given a root node reference of a BST and a key, delete the node with the given key in the BST. Return *the **root node reference** (possibly updated) of the BST*.

Basically, the deletion can be divided into two stages:

1. Search for a node to remove.
2. If the node is found, delete the node.

 

**Example 1:**

![img](./0450%20Delete%20Node%20in%20a%20BST.assets/del_node_1.jpg)

```
Input: root = [5,3,6,2,4,null,7], key = 3
Output: [5,4,6,2,null,null,7]
Explanation: Given key to delete is 3. So we find the node with value 3 and delete it.
One valid answer is [5,4,6,2,null,null,7], shown in the above BST.
Please notice that another valid answer is [5,2,6,null,4,null,7] and it's also accepted.
```

**Example 2:**

```
Input: root = [5,3,6,2,4,null,7], key = 0
Output: [5,3,6,2,4,null,7]
Explanation: The tree does not contain a node with value = 0.
```

**Example 3:**

```
Input: root = [], key = 0
Output: []
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[0, 104]`.
- `-105 <= Node.val <= 105`
- Each node has a **unique** value.
- `root` is a valid binary search tree.
- `-105 <= key <= 105`

 

**Follow up:** Could you solve it with time complexity `O(height of tree)`?

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 有点复杂

- 删除二叉树的节点
  - 没找到节点
  - 叶子节点 左空右空
  - 左不空右空
  - 左空右不空
  - 左不空右不空 （把左子树接到右子树）-> 在右子树一直向左直到找到最小值，把原来的左子树接到这个最小值的左侧，就达到了删除父节点并且保持树是二叉搜索树。

- 找到目标条件，在终止条件中进行删除操作

- TODO: 普通二叉树的删除操作

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
    def deleteNode(self, root: Optional[TreeNode], key: int) -> Optional[TreeNode]:
        # return case
        # 1. 没找到
        if root is None:
            return None
        if root.val == key:
            # 2. left None right None
            if root.left is None and root.right is None:
                return None
            # 3. left None and right not None:
            elif root.left is None and root.right is not None:
                return root.right
            # 4. right None and left not None
            elif root.left is not None and root.right is None:
                return root.left
            # 5. right not None and left not None
            else:
                # left subtree move to right subtree
                cur = root.right
                # Find min
                while cur.left: 
                    cur = cur.left
                # Now cur.left is None
                cur.left = root.left
                # delete root
                return root.right
        # recursion
        if root.val > key:
            root.left = self.deleteNode(root.left, key)
        if root.val < key:
            root.right = self.deleteNode(root.right, key)
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
