# 491. Non-decreasing Subsequences

## Problem

*****

Given an integer array `nums`, return *all the different possible non-decreasing subsequences of the given array with at least two elements*. You may return the answer in **any order**.

 

**Example 1:**

```
Input: nums = [4,6,7,7]
Output: [[4,6],[4,6,7],[4,6,7,7],[4,7],[4,7,7],[6,7],[6,7,7],[7,7]]
```

**Example 2:**

```
Input: nums = [4,4,3,2,1]
Output: [[4,4]]
```

 

**Constraints:**

- `1 <= nums.length <= 15`
- `-100 <= nums[i] <= 100`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 backtracking

### 1. Explanation

题解：

https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0491.%E9%80%92%E5%A2%9E%E5%AD%90%E5%BA%8F%E5%88%97.md#%E6%80%9D%E8%B7%AF



### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        self.result = []
        self.path = []

    def backtracking(self, nums: List[int], startIndex: int) -> None:
        # return case.
        if len(self.path) >= 2:
            self.result.append(self.path[:])
        if startIndex >= len(nums):
            return
        usedSet = set()
        for i in range(startIndex, len(nums)):
            if len(self.path) > 0 and nums[i] < self.path[-1] or nums[i] in usedSet:
                continue
            self.path.append(nums[i])
            usedSet.add(nums[i])
            self.backtracking(nums, i + 1)
            self.path.pop()
        return

    def findSubsequences(self, nums: List[int]) -> List[List[int]]:
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
