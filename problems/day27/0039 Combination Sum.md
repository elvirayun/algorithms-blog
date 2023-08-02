# 39. Combination Sum

## Problem

*****

- Given an array of **distinct** integers `candidates` and a target integer `target`, return *a list of all **unique combinations** of* `candidates` *where the chosen numbers sum to* `target`*.* You may return the combinations in **any order**.

  The **same** number may be chosen from `candidates` an **unlimited number of times**. Two combinations are unique if the 

  frequency

   of at least one of the chosen numbers is different.

  

  The test cases are generated such that the number of unique combinations that sum up to `target` is less than `150` combinations for the given input.

   

  **Example 1:**

  ```
  Input: candidates = [2,3,6,7], target = 7
  Output: [[2,2,3],[7]]
  Explanation:
  2 and 3 are candidates, and 2 + 2 + 3 = 7. Note that 2 can be used multiple times.
  7 is a candidate, and 7 = 7.
  These are the only two combinations.
  ```

  **Example 2:**

  ```
  Input: candidates = [2,3,5], target = 8
  Output: [[2,2,2,2],[2,3,3],[3,5]]
  ```

  **Example 3:**

  ```
  Input: candidates = [2], target = 1
  Output: []
  ```

   

  **Constraints:**

  - `1 <= candidates.length <= 30`
  - `2 <= candidates[i] <= 40`
  - All elements of `candidates` are **distinct**.
  - `1 <= target <= 40`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 backtracking

### 1. Explanation

- 回溯算法
- 当暴力解法可能出现无限个for循环的时候，可以使用回溯算法
- 本题和之前题目的不同是可以重复使用元素，所以每次传入的startIndex还是i



### 2. Important details

- 注意Return case的时候当sum > target的时候要返回，不然会出现死循环



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

    def backtracking(self, candidates: List[int], target:int, startIndex: int) -> None:
        # Return case.
        # 当self.sum > target 时要及时返回
        if self.sum > target:
            return
        if self.sum == target:
            self.result.append(self.path[:])
            return
        # Single layer logic.
        for i in range(startIndex, len(candidates)):
            self.path.append(candidates[i])
            self.sum += candidates[i]
            # Becasue the number can be duplicate, so startIndex still is i.
            self.backtracking(candidates, target, i)
            self.path.pop()
            self.sum -= candidates[i]
        return

    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        # Sort the candidates.
        if not len(candidates):
            return []
        candidates.sort()
        self.backtracking(candidates, target, 0)
        return self.result
```



********

## Solution2 回溯法剪枝

### 1. Explanation

<img src="./0039%20Combination%20Sum.assets/20201223170730367-20230310135337214.png" alt="39.组合总和" style="zoom:50%;" />

- 剪枝关键

  ```python
              # pruning
              if sum + candidates[i] > target:
                  break
  ```

  

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
    
    def backtracking(self, candidates: List[int], target: int, sum: int, startIndex: int) -> None:
        # Return case.
        if sum == target:
            # Append copy of path, not reference of path.
            self.result.append(self.path[:])
            return
        # Single recursion layer logic.
        for i in range(startIndex, len(candidates)):
            # pruning
            if sum + candidates[i] > target:
                break
            self.path.append(candidates[i])
            sum += candidates[i]
            self.backtracking(candidates, target, sum, i)
            self.path.pop()
            sum -= candidates[i]
        return

    def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
        self.path.clear()
        self.result.clear()
        # sort candidates
        candidates.sort()
        self.backtracking(candidates, target, 0, 0)
        return self.result
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
