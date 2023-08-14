# [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)

## Problem

*****

ou are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

 

**Example 1:**

```
Input: n = 2
Output: 2
Explanation: There are two ways to climb to the top.
1. 1 step + 1 step
2. 2 steps
```

**Example 2:**

```
Input: n = 3
Output: 3
Explanation: There are three ways to climb to the top.
1. 1 step + 1 step + 1 step
2. 1 step + 2 steps
3. 2 steps + 1 step
```

 

**Constraints:**

- `1 <= n <= 45`

******

### 1. Classification



### 2. Discussion





*******

## Solution1简化版

### 1. Explanation

- 和 [0070 Climbing Stairs](0070%20Climbing%20Stairs.md) 题类似。
- 突破点是思路：
    到达第n步台阶的方法数 = 到达第 n - 1步台阶的方法数 + 到达第 n - 2 步台阶的方法数



### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        dp = [1,2]
        sum = 0
        if n <= 2:
            return dp[n - 1]
        for i in range(3, n + 1):
            sum = dp[1] + dp[0]
            dp[0] = dp[1]
            dp[1] = sum
        return sum
```



********

## Solution2 不简化DP

### 1. Explanation





### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`



### 4. Code

```python
class Solution:
    def climbStairs(self, n: int) -> int:
        if n <= 2:
            return n
        dp = [0] * (n + 1)
        dp[1] = 1
        dp[2] = 2
        for i in range(3, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2]
        return dp[n]

```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
