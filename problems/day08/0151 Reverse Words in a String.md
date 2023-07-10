# 151. Reverse Words in a String

## Problem

*****

Given an input string `s`, reverse the order of the **words**.

A **word** is defined as a sequence of non-space characters. The **words** in `s` will be separated by at least one space.

Return *a string of the words in reverse order concatenated by a single space.*

**Note** that `s` may contain leading or trailing spaces or multiple spaces between two words. The returned string should only have a single space separating the words. Do not include any extra spaces.

 

**Example 1:**

```
Input: s = "the sky is blue"
Output: "blue is sky the"
```

**Example 2:**

```
Input: s = "  hello world  "
Output: "world hello"
Explanation: Your reversed string should not contain leading or trailing spaces.
```

**Example 3:**

```
Input: s = "a good   example"
Output: "example good a"
Explanation: You need to reduce multiple spaces between two words to a single space in the reversed string.
```



**Constraints:**

- `1 <= s.length <= 104`
- `s` contains English letters (upper-case and lower-case), digits, and spaces `' '`.
- There is **at least one** word in `s`.



**Follow-up:** If the string data type is mutable in your language, can you solve it **in-place** with `O(1)` extra space?

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 思路
  - 先移除多余空格 （和27题 移除元素思路相同 使用快慢双指针）
  - 然后再反转整个字符串
  - 最后再反转单词

### 2. Important details



### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`, 不考虑将str转换为list的话，空间复杂度为`O(1)`。



### 4. Code

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        # 双指针法, 并且空间复杂为O(1), 将str转化为list, 以达到字符串可变和练习目的
        sList = list(s)

        # 1. 移除多余空格 双指针, slow and fast
        slow, fast = 0, 0
        while fast < len(sList):
            if sList[fast] != ' ':
                # if slow pointer doesn't point to the 0th index, then add a ' '(space) 
                # before the word.
                if slow != 0: 
                    sList[slow] = ' '
                    slow += 1
                # move word from fast to slow
                while fast < len(sList) and sList[fast] != ' ':
                    sList[slow] = sList[fast]
                    slow += 1
                    fast += 1
            else:
                fast += 1
        # resize
        sList = sList[:slow]

        # 2. 反转整个字符串
        s = ''.join(sList)
        s = s[::-1]

        # 3. 反转每个单词
        start, end = 0, 0
        # 左闭右开
        while end <= len(s):
            if end == len(s) or s[end] == ' ':
                s = s[:start] + s[start:end][::-1] + s[end:]
                start = end + 1
            end += 1

        return s
```



********

## Solution2

### 1. Explanation

- 直接使用库函数python代码



### 2. Important details



### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def reverseWords(self, s: str) -> str:
        # 删除前后空白
        s = s.strip()

        # 反转整个字符串
        s = s[::-1]

        # 得到每个word, 并且反转每个word, 最后用空格连接
        s = ' '.join(word[::-1] for word in s.split())

        return s
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
