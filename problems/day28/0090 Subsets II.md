# 90. Subsets II

## Problem

*****

Given an integer array `nums` that may contain duplicates, return *all possible* 

*subsets*

 *(the power set)*.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.

**Example 1:**

```
Input: nums = [1,2,2]
Output: [[],[1],[1,2],[1,2,2],[2],[2,2]]
```

**Example 2:**

```
Input: nums = [0]
Output: [[],[0]]
```

 

**Constraints:**

- `1 <= nums.length <= 10`
- `-10 <= nums[i] <= 10`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

40.组合总和II 和 78.子集, 本题就是这两道题目的结合



### 2. Important details

- if i > 0 and nums[i] == nums[i - 1] and not self.used[i-1]:
- self.used = [0] * len(nums)
- nums.sort() - 要记得排序！



### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        self.path = []
        self.result = []
        self.used = []

    def backtracking(self, nums: List[int], startIndex: int) -> None:
        self.result.append(self.path[:])
        if startIndex >= len(nums):
            return
        for i in range(startIndex, len(nums)):
            if i > 0 and nums[i] == nums[i - 1] and not self.used[i-1]:
                continue
            self.path.append(nums[i])
            self.used[i] = True
            self.backtracking(nums, i + 1)
            self.path.pop()
            self.used[i] = False

    def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
        self.result.clear()
        self.path.clear()
        self.used = [0] * len(nums)
        nums.sort()
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
