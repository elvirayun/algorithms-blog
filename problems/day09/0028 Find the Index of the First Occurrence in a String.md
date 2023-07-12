# 28. Find the Index of the First Occurrence in a String

## Problem

*****

Given two strings `needle` and `haystack`, return the index of the first occurrence of `needle`in `haystack`, or `-1` if `needle` is not part of `haystack`.

 

**Example 1:**

```
Input: haystack = "sadbutsad", needle = "sad"
Output: 0
Explanation: "sad" occurs at index 0 and 6.
The first occurrence is at index 0, so we return 0.
```

**Example 2:**

```
Input: haystack = "leetcode", needle = "leeto"
Output: -1
Explanation: "leeto" did not occur in "leetcode", so we return -1.
```

 

**Constraints:**

- `1 <= haystack.length, needle.length <= 104`
- `haystack` and `needle` consist of only lowercase English characters.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 KMP算法

### 1. Explanation

![image-20230712130047555](./0028%20Find%20the%20Index%20of%20the%20First%20Occurrence%20in%20a%20String.assets/image-20230712130047555.png)

![image-20230712130135513](./0028%20Find%20the%20Index%20of%20the%20First%20Occurrence%20in%20a%20String.assets/image-20230712130135513.png)



### 2. Important details





### 3. Complexity

TODO: 为什么时间复杂度是`O(M+N)`

- Time complexity: `O(M + N)`, 其中n为文本串长度，m为模式串长度，因为在匹配的过程中，根据前缀表不断调整匹配的位置，可以看出匹配的过程是O(n)，之前还要单独生成next数组，时间复杂度是O(m)。所以整个KMP算法的时间复杂度是O(n+m)的。
- Space complexity: `O(M)`, Next 数组



### 4. Code

```python
class Solution:
    # KMP算法，获得前缀表 Next
    def getNext(self, needle: str) -> list:
        next = [0] * len(needle)
        # j 指向前缀末尾
        # i 指向后缀末尾
        # 初始化
        j = 0
        next[0] = 0
        for i in range(1, len(needle)):
            # 处理前后缀不相同
            while j > 0 and needle[j] != needle[i]:
                j = next[j - 1]
            # 处理前后缀相同
            if needle[j] == needle[i]:
                j += 1
            next[i] = j
        return next          

    def strStr(self, haystack: str, needle: str) -> int:
        # 初始化 指向haystack和needle的指针
        p_haystack = 0
        p_needle = 0
        # 获得next数组
        next = self.getNext(needle)
        # 开始匹配, 和创建next数组过程相似
        for p_haystack in range(len(haystack)):
            while p_needle > 0 and needle[p_needle] != haystack[p_haystack]:
                p_needle = next[p_needle - 1]
            if needle[p_needle] == haystack[p_haystack]:
                p_needle += 1
            # 如果达到needle末尾，说明匹配成功
            if p_needle == len(needle):
                return p_haystack - len(needle) + 1
        # 匹配不成功返回-1
        return -1
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
