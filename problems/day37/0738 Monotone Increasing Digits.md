# [738. Monotone Increasing Digits](https://leetcode.com/problems/monotone-increasing-digits/)

## Problem

*****

An integer has **monotone increasing digits** if and only if each pair of adjacent digits `x` and `y` satisfy `x <= y`.

Given an integer `n`, return *the largest number that is less than or equal to* `n` *with **monotone increasing digits***.

 

**Example 1:**

```
Input: n = 10
Output: 9
```

**Example 2:**

```
Input: n = 1234
Output: 1234
```

**Example 3:**

```
Input: n = 332
Output: 299
```

 

**Constraints:**

- `0 <= n <= 109`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 解题思路：
  - 暴力
  - 模拟，多模拟，多举例，多考虑多种情况。
- 这题解题思路太妙了！

本题只要想清楚个例，例如98，一旦出现strNum[i - 1] > strNum[i]的情况（非单调递增），首先想让strNum[i - 1]减一，strNum[i]赋值9，这样这个整数就是89。就可以很自然想到对应的贪心解法了。

想到了贪心，还要考虑遍历顺序，只有从后向前遍历才能重复利用上次比较的结果。

最后代码实现的时候，也需要一些技巧，例如用一个flag来标记从哪里开始赋值9。

### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(M)`, m是数字的位数



### 4. Code

```python
class Solution:
    def monotoneIncreasingDigits(self, n: int) -> int:
        digits = [int(d) for d in str(n)]
        flag = len(digits)
        # 从后往前遍历, 到index = 1 位，因为比较index和index -1
        for index in range(len(digits) - 1, 0, -1):
            if digits[index - 1] > digits[index]:
                digits[index - 1] -= 1
                flag = index
        for index in range(flag, len(digits)):
            digits[index] = 9
        n = int(''.join(map(str, digits)))
        return n

```

- 详细注释版

```python
class Solution:
    def monotoneIncreasingDigits(self, N: int) -> int:
        # 将整数转换为字符串
        strNum = list(str(N))

        # 从右往左遍历字符串
        for i in range(len(strNum) - 1, 0, -1):
            # 如果当前字符比前一个字符小，说明需要修改前一个字符
            if strNum[i - 1] > strNum[i]:
                strNum[i - 1] = str(int(strNum[i - 1]) - 1)  # 将前一个字符减1
                # 将修改位置后面的字符都设置为9，因为修改前一个字符可能破坏了递增性质
                for j in range(i, len(strNum)):
                    strNum[j] = '9'

        # 将列表转换为字符串，并将字符串转换为整数并返回
        return int(''.join(strNum))
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
