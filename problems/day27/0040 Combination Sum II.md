# 40. Combination Sum II

## Problem

*****

Given a collection of candidate numbers (`candidates`) and a target number (`target`), find all unique combinations in `candidates` where the candidate numbers sum to `target`.

Each number in `candidates` may only be used **once** in the combination.

**Note:** The solution set must not contain duplicate combinations.

 

**Example 1:**

```
Input: candidates = [10,1,2,7,6,1,5], target = 8
Output: 
[
[1,1,6],
[1,2,5],
[1,7],
[2,6]
]
```

**Example 2:**

```
Input: candidates = [2,5,2,1,2], target = 5
Output: 
[
[1,2,2],
[5]
]
```

 

**Constraints:**

- `1 <= candidates.length <= 100`
- `1 <= candidates[i] <= 50`
- `1 <= target <= 30`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 回溯剪枝

### 1. Explanation

- 树枝去重和树层去重

<img src="./0040%20Combination%20Sum%20II.assets/20221021163812.png" alt="img" style="zoom:50%;" />



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
        self.sum = 0
        self.used = []
    
    def backtracking(self, candidates: List[int], target: int, startIndex: int) -> None:
        if self.sum == target:
            self.result.append(self.path[:])
            return
        for i in range(startIndex, len(candidates)):
            # 记得总和超过target去重
            if self.sum + candidates[i] > target:
                break
            # 树层去重
            if i > 0 and candidates[i] == candidates[i - 1] and self.used[i - 1] == 0:
                continue
            # 
            self.path.append(candidates[i])
            self.sum += candidates[i]
            self.used[i] = True
            self.backtracking(candidates, target, i + 1)
            self.path.pop()
            self.sum -= candidates[i]
            self.used[i] = False
        return        

    def combinationSum2(self, candidates: List[int], target: int) -> List[List[int]]:
        self.path.clear()
        self.result.clear()
        self.used = [0] * len(candidates)
        self.sum = 0
        # Sort fisrt then we can delete repeated results.
        candidates.sort()
        self.backtracking(candidates, target, 0)
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
