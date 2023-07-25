# 110. Balanced Binary Tree

## Problem

*****

Given a binary tree, determine if it is 

**height-balanced**

.



 

**Example 1:**

![img](./0110%20Balanced%20Binary%20Tree.assets/balance_1.jpg)

```
Input: root = [3,9,20,null,null,15,7]
Output: true
```

**Example 2:**

![img](./0110%20Balanced%20Binary%20Tree.assets/balance_2.jpg)

```
Input: root = [1,2,2,3,3,null,null,4,4]
Output: false
```

**Example 3:**

```
Input: root = []
Output: true
```

 

**Constraints:**

- The number of nodes in the tree is in the range `[0, 5000]`.
- `-104 <= Node.val <= 104`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 递归法

### 1. Explanation

- 后序遍历 - 递归，因为要计算高度，收集左右子树信息。



### 2. Important details

- =  and :=

  在 Python 中，单个等号（=）用于赋值操作，而冒号加等号（:=）用于赋值表达式。

  赋值操作和赋值表达式之间的主要区别在于，赋值操作本身不返回任何值，只是将右侧的值赋给左侧的变量。另一方面，赋值表达式将右侧的值赋给左侧的变量，并返回该值。

  下面的代码是无效的，因为赋值操作（=）不会返回值，因此无法用于if语句的条件：

  ```python
  if (left_height = self.get_height(root.left)) == -1:  # 错误的语法
      return -1
  ```

  然而，使用赋值表达式（:=）可以让你在同一行中完成赋值和条件检查：

  ```python
  if (left_height := self.get_height(root.left)) == -1:  # 正确的语法
      return -1
  ```

  总的来说，冒号加等号（:=）允许你在执行赋值的同时，返回并使用该值。这在某些情况下，可以帮助你编写更简洁的代码。



### 3. Complexity

- Time complexity : O(n)

  For every subtree, we compute its height in constant time as well as
  compare the height of its children.
- Space complexity : O(n). The recursion stack may go up to O(n) if the tree is unbalanced.



### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def isBalanced(self, root: Optional[TreeNode]) -> bool:
        return False if self.getHeight(root) == -1 else True

    def getHeight(self, node: Optional[TreeNode]) -> int:
        # Post Order traversal.
        # 出口
        if not node:
            return 0
        # 
        if (leftHeight := self.getHeight(node.left)) == -1:
            return -1
        if (rightHeight := self.getHeight(node.right)) == -1:
            return -1
        # Check if it's a balanced tree.
        if abs(leftHeight - rightHeight) > 1:
            return -1
        else:
            return 1 + max(leftHeight, rightHeight)
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
