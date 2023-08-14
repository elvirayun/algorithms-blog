# [509. Fibonacci Number](https://leetcode.com/problems/fibonacci-number/)

## Problem

*****

The **Fibonacci numbers**, commonly denoted `F(n)` form a sequence, called the **Fibonacci sequence**, such that each number is the sum of the two preceding ones, starting from `0` and `1`. That is,

```
F(0) = 0, F(1) = 1
F(n) = F(n - 1) + F(n - 2), for n > 1.
```

Given `n`, calculate `F(n)`.

 

**Example 1:**

```
Input: n = 2
Output: 1
Explanation: F(2) = F(1) + F(0) = 1 + 0 = 1.
```

**Example 2:**

```
Input: n = 3
Output: 2
Explanation: F(3) = F(2) + F(1) = 1 + 1 = 2.
```

**Example 3:**

```
Input: n = 4
Output: 3
Explanation: F(4) = F(3) + F(2) = 2 + 1 = 3.
```

 

**Constraints:**

- `0 <= n <= 30`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 dp

### 1. Explanation

- 动规五部曲

这里我们要用一个一维dp数组来保存递归的结果

1. 确定dp数组以及下标的含义

dp[i]的定义为：第i个数的斐波那契数值是dp[i]

1. 确定递推公式

为什么这是一道非常简单的入门题目呢？

**因为题目已经把递推公式直接给我们了：状态转移方程 dp[i] = dp[i - 1] + dp[i - 2];**

1. dp数组如何初始化

**题目中把如何初始化也直接给我们了，如下：**

```
dp[0] = 0;
dp[1] = 1;
```



1. 确定遍历顺序

从递归公式dp[i] = dp[i - 1] + dp[i - 2];中可以看出，dp[i]是依赖 dp[i - 1] 和 dp[i - 2]，那么遍历的顺序一定是从前到后遍历的

1. 举例推导dp数组

按照这个递推公式dp[i] = dp[i - 1] + dp[i - 2]，我们来推导一下，当N为10的时候，dp数组应该是如下的数列：

0 1 1 2 3 5 8 13 21 34 55

如果代码写出来，发现结果不对，就把dp数组打印出来看看和我们推导的数列是不是一致的。



### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`

 

### 4. Code

```python
class Solution:
    def fib(self, n: int) -> int:
        if n <= 1:
            return n
        dp = [0] * (n + 1)
        dp[0] = 0
        dp[1] = 1
        for i in range(2, n + 1):
            dp[i] = dp[i - 1] + dp[i - 2]
        print(dp)
        return dp[n]
```



********

## Solution2 dp 简化

### 1. Explanation

- 只需要保存前面两个值。

### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def fib(self, n: int) -> int:
        if n <= 1:
            return n
        dp = [0, 1]
        sum = 0
        for i in range(2, n + 1):
            sum = dp[0] + dp[1]
            dp[0] = dp[1]
            dp[1] = sum
        return sum

```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
