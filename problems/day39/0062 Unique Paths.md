# [62. Unique Paths](https://leetcode.com/problems/unique-paths/)

## Problem

*****

There is a robot on an `m x n` grid. The robot is initially located at the **top-left corner** (i.e., `grid[0][0]`). The robot tries to move to the **bottom-right corner** (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

Given the two integers `m` and `n`, return *the number of possible unique paths that the robot can take to reach the bottom-right corner*.

The test cases are generated so that the answer will be less than or equal to `2 * 109`.

 

**Example 1:**

![img](./0062%20Unique%20Paths.assets/robot_maze.png)

```
Input: m = 3, n = 7
Output: 28
```

**Example 2:**

```
Input: m = 3, n = 2
Output: 3
Explanation: From the top-left corner, there are a total of 3 ways to reach the bottom-right corner:
1. Right -> Down -> Down
2. Down -> Down -> Right
3. Down -> Right -> Down
```

 

**Constraints:**

- `1 <= m, n <= 100`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 动规五部曲 ：

  ```python
  dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
  ```

  



### 2. Important details





### 3. Complexity

- Time complexity: `O(m * n)`
- Space complexity: `O(m * n)`



### 4. Code

```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        # m * n matrix.
        # The number of unique paths to reach the dp[i][j]
        dp = [[0 for _ in range(n)] for _ in range(m)]
        # initial
        for i in range(m):
            dp[i][0] = 1
        for j in range(n):
            dp[0][j] = 1

        for j in range(1, n):
            for i in range(1, m):
                dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        return dp[m - 1][n - 1]
```



********

## Solution2 dp simplified

### 1. Explanation

![IMG_0638](./0062%20Unique%20Paths.assets/IMG_0638.jpg)



### 2. Important details





### 3. Complexity

- Time complexity: `O(m * n)`
- Space complexity: `O(n)`



### 4. Code

```python
class Solution:
    def uniquePaths(self, m: int, n: int) -> int:
        dp = [1 for _ in range(n)]

        for i in range(1, m):
            for j in range(1, n):
                dp[j] += dp[j - 1]

        return dp[n - 1]
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
