# [746. Min Cost Climbing Stairs](https://leetcode.com/problems/min-cost-climbing-stairs/)

## Problem

*****

You are given an integer array `cost` where `cost[i]` is the cost of `ith` step on a staircase. Once you pay the cost, you can either climb one or two steps.

You can either start from the step with index `0`, or the step with index `1`.

Return *the minimum cost to reach the top of the floor*.

 

**Example 1:**

```
Input: cost = [10,15,20]
Output: 15
Explanation: You will start at index 1.
- Pay 15 and climb two steps to reach the top.
The total cost is 15.
```

**Example 2:**

```
Input: cost = [1,100,1,1,1,100,1,1,100,1]
Output: 6
Explanation: You will start at index 0.
- Pay 1 and climb two steps to reach index 2.
- Pay 1 and climb two steps to reach index 4.
- Pay 1 and climb two steps to reach index 6.
- Pay 1 and climb one step to reach index 7.
- Pay 1 and climb two steps to reach index 9.
- Pay 1 and climb one step to reach the top.
The total cost is 6.
```

 

**Constraints:**

- `2 <= cost.length <= 1000`
- `0 <= cost[i] <= 999`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 DP

### 1. Explanation

**dp[i]的定义：到达第i台阶所花费的最少体力为dp[i]**。

**可以有两个途径得到dp[i]，一个是dp[i-1] 一个是dp[i-2]**。

dp[i - 1] 跳到 dp[i] 需要花费 dp[i - 1] + cost[i - 1]。

dp[i - 2] 跳到 dp[i] 需要花费 dp[i - 2] + cost[i - 2]。

那么究竟是选从dp[i - 1]跳还是从dp[i - 2]跳呢？

一定是选最小的，所以dp[i] = min(dp[i - 1] + cost[i - 1], dp[i - 2] + cost[i - 2]);


- 题目  [0509 Fibonacci Number](0509%20Fibonacci%20Number.md) 和 [0070 Climbing Stairs](0070%20Climbing%20Stairs.md)  的进阶版
### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`



### 4. Code

```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        top_index = len(cost)
        # dp[i]: minimum cost to arrive step i.
        dp = [0] * (top_index + 1)
        dp[0] = 0
        dp[1] = 0
        for i in range(2, len(dp)):
            dp[i] = min(dp[i - 1] + cost[i - 1], dp[i - 2] + cost[i - 2])
        return dp[top_index]

```



********

## Solution2 化简DP

### 1. Explanation





### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def minCostClimbingStairs(self, cost: List[int]) -> int:
        top_index = len(cost)
        min_cost = 0
        dp = [0, 0]
        for i in range(2, top_index + 1):
            min_cost = min(dp[1] + cost[i - 1], dp[0] + cost[i - 2])
            dp[0] = dp[1]
            dp[1] = min_cost
        return min_cost

```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
