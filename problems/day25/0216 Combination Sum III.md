# 216. Combination Sum III

## Problem

*****

Find all valid combinations of `k` numbers that sum up to `n` such that the following conditions are true:

- Only numbers `1` through `9` are used.
- Each number is used **at most once**.

Return *a list of all possible valid combinations*. The list must not contain the same combination twice, and the combinations may be returned in any order.

 

**Example 1:**

```
Input: k = 3, n = 7
Output: [[1,2,4]]
Explanation:
1 + 2 + 4 = 7
There are no other valid combinations.
```

**Example 2:**

```
Input: k = 3, n = 9
Output: [[1,2,6],[1,3,5],[2,3,4]]
Explanation:
1 + 2 + 6 = 9
1 + 3 + 5 = 9
2 + 3 + 4 = 9
There are no other valid combinations.
```

**Example 3:**

```
Input: k = 4, n = 1
Output: []
Explanation: There are no valid combinations.
Using 4 different numbers in the range [1,9], the smallest sum we can get is 1+2+3+4 = 10 and since 10 > 1, there are no valid combination.
```

 

**Constraints:**

- `2 <= k <= 9`
- `1 <= n <= 60`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 回溯不剪枝

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
    
    def backtracking(self, k:int, n:int, startIndex: int) -> None:
        if len(self.path) == k:
            if sum(self.path) == n:
                self.result.append(self.path[:])
            return
        for i in range(startIndex, 10):
            self.path.append(i)
            self.backtracking(k, n, i + 1)
            self.path.pop()
        return

    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        self.backtracking(k, n, 1)
        return self.result
```



********

## Solution2 回溯剪枝

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
    
    def backtracking(self, k:int, targetSum:int, currentSum: int, startIndex: int) -> None:
        # 剪枝sum 都是正整数
        if currentSum > targetSum:
            return
        if len(self.path) == k:
            if sum(self.path) == targetSum:
                self.result.append(self.path[:])
            return
        # 剪枝 10 - (k - len(self.path)) + 1 + 1
        for i in range(startIndex, 9 - (k - len(self.path)) + 1 + 1 ):
            self.path.append(i)
            currentSum += i
            self.backtracking(k, targetSum, currentSum,i + 1)
            self.path.pop()
            currentSum -= i
        return

    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        self.backtracking(k, n, 0, 1)
        return self.result
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
