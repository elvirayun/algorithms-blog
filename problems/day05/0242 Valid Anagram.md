# 242. Valid Anagram

## Problem

*****

Given two strings `s` and `t`, return `true` *if* `t` *is an anagram of* `s`*, and* `false`*otherwise*.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.

 

**Example 1:**

```
Input: s = "anagram", t = "nagaram"
Output: true
```

**Example 2:**

```
Input: s = "rat", t = "car"
Output: false
```

 

**Constraints:**

- `1 <= s.length, t.length <= 5 * 104`
- `s` and `t` consist of lowercase English letters.

 

**Follow up:** What if the inputs contain Unicode characters? How would you adapt your solution to such a case?

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 用数组构造Hash Table.
- 记录字符出现的次数，用 +1 和 -1 的方式方便快捷的进行比较
- ASCII码/ord()的使用 - [python 中的ASCII码](https://www.runoob.com/python3/python3-ascii-character.html)



### 2. Important details

- [python ord()](https://www.programiz.com/python-programming/methods/built-in/ord)

- [python defaultdict](https://www.geeksforgeeks.org/defaultdict-in-python/#)
- [Python Counter](https://www.geeksforgeeks.org/python-counter-objects-elements/)



### 3. Complexity

- Time complexity: `O(N)`

- Space complexity: `O(1)` : 空间上因为定义是的一个常量大小的辅助数组，所以空间复杂度为`O(1)`

  

### 4. Code

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        # hash table
        record = [0] * 26
        for i in s:
            record[ord(i) - ord("a")] += 1
        for i in t:
            record[ord(i) - ord("a")] -= 1
        for i in range(26):
            if record[i] != 0:
                return False
        return True
```



- python defaultdict: python defaultdict 就是一个map。

```python
class Solution:
    def isAnagram(self, s: str, t: str) -> bool:
        from collections import defaultdict
        
        s_dict = defaultdict(int)
        t_dict = defaultdict(int)

        for i in s:
            s_dict[i] += 1
        for i in t:
            t_dict[i] += 1
        
        return s_dict == t_dict
```



- Python Counter 是一种 data set

  ```python
  class Solution:
      def isAnagram(self, s: str, t: str) -> bool:
          from collections import Counter
  
          s_count = Counter(s)
          t_count = Counter(t)
  
          return s_count == t_count
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
