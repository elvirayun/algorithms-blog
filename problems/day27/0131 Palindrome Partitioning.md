# 131. Palindrome Partitioning

## Problem

*****

Given a string `s`, partition `s` such that every 

substring

 of the partition is a 

**palindrome**

. Return *all possible palindrome partitioning of* `s`.

 

**Example 1:**

```
Input: s = "aab"
Output: [["a","a","b"],["aa","b"]]
```

**Example 2:**

```
Input: s = "a"
Output: [["a"]]
```

 

**Constraints:**

- `1 <= s.length <= 16`
- `s` contains only lowercase English letters.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

[题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0131.%E5%88%86%E5%89%B2%E5%9B%9E%E6%96%87%E4%B8%B2.md)

- 切割问题可以抽象为组合问题
- 如何模拟那些切割线
- 切割问题中递归如何终止
- 在递归循环中如何截取子串
- 如何判断回文

**本题我相信很多同学主要卡在了第一个难点上：就是不知道如何切割，甚至知道要用回溯法，也不知道如何用。也就是没有体会到按照求组合问题的套路就可以解决切割**。

如果意识到这一点，算是重大突破了。接下来就可以对着模板照葫芦画瓢。

**但接下来如何模拟切割线，如何终止，如何截取子串，其实都不好想，最后判断回文算是最简单的了**。

关于模拟切割线，其实就是index是上一层已经确定了的分割线，i是这一层试图寻找的新分割线

除了这些难点，**本题还有细节，例如：切割过的地方不能重复切割所以递归函数需要传入i + 1**。

![131.分割回文串](./0131%20Palindrome%20Partitioning.assets/68747470733a2f2f636f64652d7468696e6b696e672e63646e2e626365626f732e636f6d2f706963732f3133312e2545352538382538362545352538392542322545352539422539452545362539362538372545342542382542322e6a7067.jpeg)

### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        self.path = []
        self.result = []
    
    def isPalindrome(self, s:str, start, end) -> bool:
        while start < end:
            if s[start] != s[end]:
                return False
            start += 1
            end -= 1
        return True

    def backtracking(self, s:str, startIndex: int) -> None:
        if startIndex == len(s):
            self.result.append(self.path[:])
            return
        # Single layer.
        for i in range(startIndex, len(s)):
            if self.isPalindrome(s, startIndex, i):
                # collect path.
                self.path.append(s[startIndex:i+1])
                self.backtracking(s, i+1)
                self.path.pop()
        return

    def partition(self, s: str) -> List[List[str]]:
        self.path.clear()
        self.result.clear()
        self.backtracking(s, 0)
        return self.result
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
