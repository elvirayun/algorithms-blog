# [63. Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)

## Problem

*****

You are given an `m x n` integer array `grid`. There is a robot initially located at the **top-left corner** (i.e., `grid[0][0]`). The robot tries to move to the **bottom-right corner** (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

An obstacle and space are marked as `1` or `0` respectively in `grid`. A path that the robot takes cannot include **any** square that is an obstacle.

Return *the number of possible unique paths that the robot can take to reach the bottom-right corner*.

The testcases are generated so that the answer will be less than or equal to `2 * 109`.

 

**Example 1:**

![img](./0063%20Unique%20Paths%20II.assets/robot1.jpg)

```
Input: obstacleGrid = [[0,0,0],[0,1,0],[0,0,0]]
Output: 2
Explanation: There is one obstacle in the middle of the 3x3 grid above.
There are two ways to reach the bottom-right corner:
1. Right -> Right -> Down -> Down
2. Down -> Down -> Right -> Right
```

**Example 2:**

![img](./0063%20Unique%20Paths%20II.assets/robot2.jpg)

```
Input: obstacleGrid = [[0,1],[0,0]]
Output: 1
```

 

**Constraints:**

- `m == obstacleGrid.length`
- `n == obstacleGrid[i].length`
- `1 <= m, n <= 100`
- `obstacleGrid[i][j]` is `0` or `1`.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

-  [0062 Unique Paths](0062%20Unique%20Paths.md)  题的障碍版
-  只要把有障碍的值赋值为0即可，注意第0行和第0列障碍之后的值都是0


### 2. Important details

-  注意遍历的起止范围，容易出错。

### 3. Complexity

- Time complexity: `O( m * n)`
- Space complexity: `O(m * n)`


### 4. Code

```python

class Solution:
    def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
        # m * n matrix
        m = len(obstacleGrid)
        n = len(obstacleGrid[0])
        obstacle = 1
        # The number of unique paths to reach the dp[i][j]
        dp = [[ -1 for _ in range(n)] for _ in range(m)]
        # initial
        dp[0][0] = 1
        #
        for i in range(0, m):
            for j in range(0, n):
                if obstacleGrid[i][j] == obstacle:
                    dp[i][j] = 0
                else:
                    if j >= 1 and i == 0:
                        dp[i][j] = dp[i][j - 1]
                    if i >= 1 and j == 0:
                        dp[i][j] = dp[i - 1][j]
                    if i >= 1 and j >= 1:
                        dp[i][j] = dp[i - 1][j] + dp[i][j - 1]
        #
        return dp[m - 1][n - 1]

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
