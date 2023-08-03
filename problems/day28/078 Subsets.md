# 78. Subsets

## Problem

*****

Given an integer array `nums` of **unique** elements, return *all possible* 

*subsets*

 *(the power set)*.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

**Example 1:**

```
Input: nums = [1,2,3]
Output: [[],[1],[2],[1,2],[3],[1,3],[2,3],[1,2,3]]
```

**Example 2:**

```
Input: nums = [0]
Output: [[],[0]]
```

**Constraints:**

- `1 <= nums.length <= 10`
- `-10 <= nums[i] <= 10`
- All the numbers of `nums` are **unique**.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 和其他题目类似，不过是收集每个节点的结果，包括更节点
- 注意for 循环时只选择当前值之后的值！！



### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        self.path = []
        self.result = []
        
    def backtracking(self, nums: List[int], startIndex: int) -> None:
        # 在终止条件之前收集保证收集到最后一层结果
        self.result.append(self.path[:])
        # 终止条件
        if startIndex >= len(nums):
            return
        for i in range(startIndex, len(nums)):
            self.path.append(nums[i])
            self.backtracking(nums, i + 1)
            self.path.pop()
        return

    def subsets(self, nums: List[int]) -> List[List[int]]:
        self.result.clear()
        self.path.clear()
        self.backtracking(nums, 0)
        return self.result
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
