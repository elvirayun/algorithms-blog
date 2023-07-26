# 654. Maximum Binary Tree

## Problem

*****

You are given an integer array `nums` with no duplicates. A **maximum binary tree**can be built recursively from `nums` using the following algorithm:

1. Create a root node whose value is the maximum value in `nums`.
2. Recursively build the left subtree on the **subarray prefix** to the **left** of the maximum value.
3. Recursively build the right subtree on the **subarray suffix** to the **right** of the maximum value.

Return *the **maximum binary tree** built from* `nums`.

 

**Example 1:**

![img](./0654%20Maximum%20Binary%20Tree.assets/tree1.jpg)

```
Input: nums = [3,2,1,6,0,5]
Output: [6,3,5,null,2,0,null,null,1]
Explanation: The recursive calls are as follow:
- The largest value in [3,2,1,6,0,5] is 6. Left prefix is [3,2,1] and right suffix is [0,5].
    - The largest value in [3,2,1] is 3. Left prefix is [] and right suffix is [2,1].
        - Empty array, so no child.
        - The largest value in [2,1] is 2. Left prefix is [] and right suffix is [1].
            - Empty array, so no child.
            - Only one element, so child is a node with value 1.
    - The largest value in [0,5] is 5. Left prefix is [0] and right suffix is [].
        - Only one element, so child is a node with value 0.
        - Empty array, so no child.
```

**Example 2:**

![img](./0654%20Maximum%20Binary%20Tree.assets/tree2.jpg)

```
Input: nums = [3,2,1]
Output: [3,null,2,null,1]
```

 

**Constraints:**

- `1 <= nums.length <= 1000`
- `0 <= nums[i] <= 1000`
- All integers in `nums` are **unique**.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 前序遍历 ➕ 递归

### 1. Explanation

- 前序遍历 ➕ 递归 ➕ 切片
- 注意区间保持一致，要么左闭右开，要么左闭右闭。

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
    def constructMaximumBinaryTree(self, nums: List[int]) -> Optional[TreeNode]:
        return self.traversal(nums, 0, len(nums))
    # 1. 设置参数和返回值
    def traversal(self, nums: List[int], left: int, right: int) -> Optional[TreeNode]:
        # 2. 设置终止条件
        if left == right:
            return None
        # 3. 单层递归逻辑
        # Find max value and index of it.
        maxValueIndex = left
        for i in range(left + 1, right):
            if nums[i] > nums[maxValueIndex]:
                maxValueIndex = i
        root = TreeNode(nums[maxValueIndex])
        root.left = self.traversal(nums, left, maxValueIndex)
        root.right = self.traversal(nums, maxValueIndex + 1, right)
        return root
```



********

## Solution2 前序遍历➕递归➕Python切片

### 1. Explanation

- 灵活使用Python切片

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
    def constructMaximumBinaryTree(self, nums: List[int]) -> Optional[TreeNode]:
        return self.traversal(nums)
    # 1. 设置参数和返回值
    def traversal(self, nums: List[int]) -> Optional[TreeNode]:
        # 2. 设置终止条件
        if len(nums) == 0:
            return None
        # 3. 单层递归逻辑
        # Find max value and index of it.
        maxValueIndex = 0
        for i in range(1, len(nums)):
            if nums[i] > nums[maxValueIndex]:
                maxValueIndex = i
        root = TreeNode(nums[maxValueIndex])
        root.left = self.traversal(nums[:maxValueIndex])
        root.right = self.traversal(nums[maxValueIndex + 1:])
        return root
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
