# [1049. Last Stone Weight II](https://leetcode.com/problems/last-stone-weight-ii/)

## Problem

*****

You are given an array of binary strings `strs` and two integers `m` and `n`.

Return *the size of the largest subset of `strs` such that there are **at most*** `m` `0`*'s and* `n` `1`*'s in the subset*.

A set `x` is a **subset** of a set `y` if all elements of `x` are also elements of `y`.

 

**Example 1:**

```
Input: strs = ["10","0001","111001","1","0"], m = 5, n = 3
Output: 4
Explanation: The largest subset with at most 5 0's and 3 1's is {"10", "0001", "1", "0"}, so the answer is 4.
Other valid but smaller subsets include {"0001", "1"} and {"10", "1", "0"}.
{"111001"} is an invalid subset because it contains 4 1's, greater than the maximum of 3.
```

**Example 2:**

```
Input: strs = ["10","0","1"], m = 1, n = 1
Output: 2
Explanation: The largest subset is {"0", "1"}, so the answer is 2.
```

 

**Constraints:**

- `1 <= strs.length <= 600`
- `1 <= strs[i].length <= 100`
- `strs[i]` consists only of digits `'0'` and `'1'`.
- `1 <= m, n <= 100`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 二重01 背包

### 1. Explanation





### 2. Important details





### 3. Complexity

- Time complexity:  `O(KMN)`, K is the length of strs.
- Space complexity: `O(MN)`



### 4. Code

```python
class Solution:
    def findMaxForm(self, strs: List[str], m: int, n: int) -> int:
        # dp m + 1 * n + 1
        dp = [[0 for _ in range(n + 1)] for _ in range(m + 1)]
        dp[0][0] = 0
        for str in strs:
            zeroNum, oneNum = 0, 0
            # 
            for char in str:
                if char == '0':
                    zeroNum += 1
                else:
                    oneNum += 1
            #
            print(zeroNum, oneNum)
            for i in range(m, zeroNum - 1, -1):
                for j in range(n, oneNum - 1, -1):
                    dp[i][j] = max(dp[i][j], dp[i - zeroNum][j - oneNum] + 1)
        return dp[m][n]

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
