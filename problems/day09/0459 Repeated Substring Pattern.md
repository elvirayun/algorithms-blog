# 459. Repeated Substring Pattern

## Problem

*****

Given a string `s`, check if it can be constructed by taking a substring of it and appending multiple copies of the substring together.



**Example 1:**

```
Input: s = "abab"
Output: true
Explanation: It is the substring "ab" twice.
```

**Example 2:**

```
Input: s = "aba"
Output: false
```

**Example 3:**

```
Input: s = "abcabcabcabc"
Output: true
Explanation: It is the substring "abc" four times or the substring "abcabc" twice. 
```

**Constraints:**

- `1 <= s.length <= 104`
- `s` consists of lowercase English letters.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 KMP算法

### 1. Explanation

- [459题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0459.%E9%87%8D%E5%A4%8D%E7%9A%84%E5%AD%90%E5%AD%97%E7%AC%A6%E4%B8%B2.md)
- TODO: 这题要多复习多理解

最长相等前后缀的长度为：next[len - 1] + 1。(这里的next数组是以统一减一的方式计算的，因此需要+1，两种计算next数组的具体区别看这里：[字符串：KMP算法精讲 (opens new window)](https://programmercarl.com/0028.实现strStr.html))

数组长度为：len。

如果len % (len - (next[len - 1] + 1)) == 0 ，则说明数组的长度正好可以被 (数组长度-最长相等前后缀的长度) 整除 ，说明该字符串有重复的子字符串。

**数组长度减去最长相同前后缀的长度相当于是第一个周期的长度，也就是一个周期的长度，如果这个周期可以被整除，就说明整个数组就是这个周期的循环。**

### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`



### 4. Code

```python
class Solution:
    # KMP算法
    def getNext(self, s: str) -> list:
        next = [0] * len(s)
        j = 0
        next[0] = 0
        for i in range(1, len(s)):
            while j > 0 and s[j] != s[i]:
                j = next[j - 1]
            if s[j] == s[i]:
                j +=1
            next[i] = j
        return next

    def repeatedSubstringPattern(self, s: str) -> bool:
        if len(s) == 0:
            return False
        next = self.getNext(s)
        if next[-1] != 0 and len(s) % (len(s) - next[-1]) == 0:
            return True
        return False
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
