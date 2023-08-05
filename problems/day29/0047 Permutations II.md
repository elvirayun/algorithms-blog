# [47. Permutations II](https://leetcode.com/problems/permutations-ii/)

## Problem

*****

Given a collection of numbers, `nums`, that might contain duplicates, return *all possible unique permutations **in any order**.*

 

**Example 1:**

```
Input: nums = [1,1,2]
Output:
[[1,1,2],
 [1,2,1],
 [2,1,1]]
```

**Example 2:**

```
Input: nums = [1,2,3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

 

**Constraints:**

- `1 <= nums.length <= 8`
- `-10 <= nums[i] <= 10`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 一个带入回溯过程的usedSet
- 一个记录单层重复的usedInLayer

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
        self.usedSet = []

    def backtracking(self, nums: List[int]) -> None:
        usedinLayer = set()
        if len(self.path) == len(nums):
            self.result.append(self.path[:])
            return
        for i in range(len(nums)):
            if self.usedSet[i]  or nums[i] in usedinLayer:
                continue
            usedinLayer.add(nums[i])
            self.path.append(nums[i])
            self.usedSet[i] = True
            self.backtracking(nums)
            self.path.pop()
            self.usedSet[i] = False
        return

    def permuteUnique(self, nums: List[int]) -> List[List[int]]:
        self.path.clear()
        self.result.clear()
        self.usedSet = [0] * len(nums)
        self.backtracking(nums)
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
