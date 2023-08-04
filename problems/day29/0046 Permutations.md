# 46. Permutations

## Problem

*****

Given an array `nums` of distinct integers, return *all the possible permutations*. You can return the answer in **any order**.

 

**Example 1:**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**Example 2:**

```
Input: nums = [0,1]
Output: [[0,1],[1,0]]
```

**Example 3:**

```
Input: nums = [1]
Output: [[1]]
```

 

**Constraints:**

- `1 <= nums.length <= 6`
- `-10 <= nums[i] <= 10`
- All the integers of `nums` are **unique**.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation





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
        self.usedSet = set()

    def backtracking(self, nums: List[int]) -> None:
        if len(self.path) == len(nums):
            self.result.append(self.path[:])
            return
        for i in range(len(nums)):
            if nums[i] in self.usedSet:
                continue
            self.path.append(nums[i])
            self.usedSet.add(nums[i])
            self.backtracking(nums)
            self.path.pop()
            self.usedSet.discard(nums[i])
        return

    def permute(self, nums: List[int]) -> List[List[int]]:
        self.path.clear()
        self.result.clear()
        self.usedSet.clear()
        self.backtracking(nums)
        return self.result
```



********

## Solution2

### 1. Explanation





### 2. Important details

[[0491 Non-decreasing Subsequences]]
[Template 1](Template%201.md)

### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python

```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
