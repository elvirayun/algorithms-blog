# [96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)

## Problem

*****

Given an integer `n`, return *the number of structurally unique **BST'**s (binary search trees) which has exactly* `n` *nodes of unique values from* `1` *to* `n`.

 

**Example 1:**

![img](./0096%20Unique%20Binary%20Search%20Trees.assets/uniquebstn3-20230814234139230.jpg)

```
Input: n = 3
Output: 5
```

**Example 2:**

```
Input: n = 1
Output: 1
```

 

**Constraints:**

- `1 <= n <= 19`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

题解：

https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0096.%E4%B8%8D%E5%90%8C%E7%9A%84%E4%BA%8C%E5%8F%89%E6%90%9C%E7%B4%A2%E6%A0%91.md



### 2. Important details





### 3. Complexity

- Time complexity: `O(N ^ 2)`
- Space complexity: `O(N)`



### 4. Code

```python
class Solution:
    def numTrees(self, n: int) -> int:
        dp = [0] * (n + 1)
        dp[0] = 1
        for i in range(1, n + 1):
            for j in range(1, i + 1):
                dp[i] += dp[j - 1] * dp[i - j]
        return dp[n]

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
