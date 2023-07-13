# 1047. Remove All Adjacent Duplicates In String

## Problem

*****

You are given a string `s` consisting of lowercase English letters. A **duplicate removal**consists of choosing two **adjacent** and **equal** letters and removing them.

We repeatedly make **duplicate removals** on `s` until we no longer can.

Return *the final string after all such duplicate removals have been made*. It can be proven that the answer is **unique**.

 

**Example 1:**

```
Input: s = "abbaca"
Output: "ca"
Explanation: 
For example, in "abbaca" we could remove "bb" since the letters are adjacent and equal, and this is the only possible move.  The result of this move is that the string is "aaca", of which only "aa" is possible, so the final string is "ca".
```

**Example 2:**

```
Input: s = "azxxzy"
Output: "ay"
```

 

**Constraints:**

- `1 <= s.length <= 105`
- `s` consists of lowercase English letters.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 Using stack

### 1. Explanation

- 直接使用栈来判断和消除非常快
- 遍历元素，如果当前元素和栈顶元素相等，则弹出栈顶元素即可。

![1047.删除字符串中的所有相邻重复项](./0047%20Remove%20All%20Adjacent%20Duplicates%20In%20String.assets/1047.%E5%88%A0%E9%99%A4%E5%AD%97%E7%AC%A6%E4%B8%B2%E4%B8%AD%E7%9A%84%E6%89%80%E6%9C%89%E7%9B%B8%E9%82%BB%E9%87%8D%E5%A4%8D%E9%A1%B9.gif)



### 2. Important details

- 而且**在企业项目开发中，尽量不要使用递归**！在项目比较大的时候，由于参数多，全局变量等等，使用递归很容易判断不充分return的条件，非常容易无限递归（或者递归层级过深），**造成栈溢出错误（这种问题还不好排查！）**



### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`, 栈的空间



### 4. Code

```python
class Solution:
    def removeDuplicates(self, s: str) -> str:
        stack = []
        for char in s:
            if len(stack) != 0 and char == stack[-1]:
                stack.pop()
            else:
                stack.append(char)
        return ''.join(stack)
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
