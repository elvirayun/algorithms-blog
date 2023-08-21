# [494. Target Sum](https://leetcode.com/problems/target-sum/)

## Problem

*****

You are given an integer array `nums` and an integer `target`.

You want to build an **expression** out of nums by adding one of the symbols `'+'` and `'-'` before each integer in nums and then concatenate all the integers.

- For example, if `nums = [2, 1]`, you can add a `'+'` before `2` and a `'-'` before `1` and concatenate them to build the expression `"+2-1"`.

Return the number of different **expressions** that you can build, which evaluates to `target`.

 

**Example 1:**

```
Input: nums = [1,1,1,1,1], target = 3
Output: 5
Explanation: There are 5 ways to assign symbols to make the sum of nums be target 3.
-1 + 1 + 1 + 1 + 1 = 3
+1 - 1 + 1 + 1 + 1 = 3
+1 + 1 - 1 + 1 + 1 = 3
+1 + 1 + 1 - 1 + 1 = 3
+1 + 1 + 1 + 1 - 1 = 3
```

**Example 2:**

```
Input: nums = [1], target = 1
Output: 1
```

 

**Constraints:**

- `1 <= nums.length <= 20`
- `0 <= nums[i] <= 1000`
- `0 <= sum(nums[i]) <= 1000`
- `-1000 <= target <= 1000`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 01 背包问题

### 1. Explanation





### 2. Important details





### 3. Complexity

- Time complexity: `O(M * N)`
- Space complexity: `O(N)`



### 4. Code

```python
class Solution:
    def findTargetSumWays(self, nums: List[int], target: int) -> int:
        sumOfNums = sum(nums)
        if sumOfNums < abs(target):
            return 0
        if ( sumOfNums + target ) % 2 != 0:
            return 0
        # 0 1 背包问题
        positiveSum = ( sumOfNums + target ) // 2
        dp = [0] * (positiveSum + 1)
        dp[0] = 1
        for i in range(len(nums)):
            for j in range(positiveSum, nums[i] - 1, -1):
                dp[j] += dp[j - nums[i]]
        return dp[positiveSum]
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
