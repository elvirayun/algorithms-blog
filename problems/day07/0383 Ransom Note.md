# 383. Ransom Note

## Problem

*****

Given two strings `ransomNote` and `magazine`, return `true` *if* `ransomNote` *can be constructed by using the letters from* `magazine` *and* `false` *otherwise*.

Each letter in `magazine` can only be used once in `ransomNote`.

 

**Example 1:**

```
Input: ransomNote = "a", magazine = "b"
Output: false
```

**Example 2:**

```
Input: ransomNote = "aa", magazine = "ab"
Output: false
```

**Example 3:**

```
Input: ransomNote = "aa", magazine = "aab"
Output: true
```

 

**Constraints:**

- `1 <= ransomNote.length, magazine.length <= 105`
- `ransomNote` and `magazine` consist of lowercase English letters.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 和 242.Valid Anagram 基本一致。
- 不一样的点在于只要求在ransomNote 出现过的字母在magazineh中出现过，反过来并没有要求
- 所以和242题一样的写法，当在检测到有未出现的字符时直接返回False。



### 2. Important details

- **使用map的空间消耗要比数组大一些的，因为map要维护红黑树或者哈希表，而且还要做哈希函数，是费时的！数据量大的话就能体现出来差别了。 所以数组更加简单直接有效！**
- 使用数组做 hash table



### 3. Complexity

- Time complexity: `O(N)`,  两次单独的for循环,  N是 ransomNote的长度
- Space complexity: `O(1)`, 就用了一个26长度的数组



### 4. Code

```python
class Solution:
    def canConstruct(self, ransomNote: str, magazine: str) -> bool:
        # 使用数组做hash table
        record = [0] * 26
        # 剪枝
        if len(ransomNote) > len(magazine):
            return False
        for letter in magazine:
            record[ord(letter) - ord('a')] += 1
        for letter in ransomNote:
            letter_index = ord(letter) - ord('a')
            if record[letter_index] == 0:
                return False
            else:
                record[letter_index] -= 1
        return True
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
