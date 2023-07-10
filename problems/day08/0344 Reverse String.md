# 344. Reverse String

## Problem

*****

Write a function that reverses a string. The input string is given as an array of characters `s`.

You must do this by modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm) with `O(1)` extra memory.

 

**Example 1:**

```
Input: s = ["h","e","l","l","o"]
Output: ["o","l","l","e","h"]
```

**Example 2:**

```
Input: s = ["H","a","n","n","a","h"]
Output: ["h","a","n","n","a","H"]
```



**Constraints:**

- `1 <= s.length <= 105`
- `s[i]` is a [printable ascii character](https://en.wikipedia.org/wiki/ASCII#Printable_characters).

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 双指针法： left, right分别指向最左边和最右边，交换对应字符，左右指针逐渐往中间收缩。



### 2. Important details

- 临界点看是`left < s_length // 2` 还是 `left <= s_length // 2`, 直接代入具体的数值即可



### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def reverseString(self, s: List[str]) -> None:
        """
        Do not return anything, modify s in-place instead.
        """
        s_length = len(s)
        # 双指针法
        left, right = 0, s_length - 1
        
        while left < s_length // 2:
            s[left], s[right] = s[right], s[left]
            left += 1
            right -= 1
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
