# 剑指 Offer 58 - II. 左旋转字符串

## Problem

*****

字符串的左旋转操作是把字符串前面的若干个字符转移到字符串的尾部。请定义一个函数实现字符串左旋转操作的功能。比如，输入字符串"abcdefg"和数字2，该函数将返回左旋转两位得到的结果"cdefgab"。

 

**示例 1：**

```
输入: s = "abcdefg", k = 2
输出: "cdefgab"
```

**示例 2：**

```
输入: s = "lrloseumgh", k = 6
输出: "umghlrlose"
```

 

**限制：**

- `1 <= k < s.length <= 10000`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 先反转前n个字符
- 在反转[n:] 的字符
- 最后反转整个字符串就能达到要求



### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`, 但实际上python的字符串操作会产生新的字符串



### 4. Code

```python
class Solution:
    def reverseLeftWords(self, s: str, n: int) -> str:
        s = s[:n][::-1] + s[n:][::-1]
        return s[::-1]
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
