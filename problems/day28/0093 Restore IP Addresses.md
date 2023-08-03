# 93. Restore IP Addresses

## Problem

*****

A **valid IP address** consists of exactly four integers separated by single dots. Each integer is between `0` and `255` (**inclusive**) and cannot have leading zeros.

- For example, `"0.1.2.201"` and `"192.168.1.1"` are **valid** IP addresses, but `"0.011.255.245"`, `"192.168.1.312"` and `"192.168@1.1"` are **invalid** IP addresses.

Given a string `s` containing only digits, return *all possible valid IP addresses that can be formed by inserting dots into* `s`. You are **not** allowed to reorder or remove any digits in `s`. You may return the valid IP addresses in **any** order.

 

**Example 1:**

```
Input: s = "25525511135"
Output: ["255.255.11.135","255.255.111.35"]
```

**Example 2:**

```
Input: s = "0000"
Output: ["0.0.0.0"]
```

**Example 3:**

```
Input: s = "101023"
Output: ["1.0.10.23","1.0.102.3","10.1.0.23","10.10.2.3","101.0.2.3"]
```

 

**Constraints:**

- `1 <= s.length <= 20`
- `s` consists of digits only.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

![93.复原IP地址](./0093%20Restore%20IP%20Addresses.assets/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303230313132333230333733353933332d32303233303331303133323331343130392e706e67.png)



### 2. Important details

- 在python中字符串是不可变的
- 注意在回溯中，如果加了什么东西一定要减回去！！！



### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
# 回溯算法
# four integers
# [0,255]
# 分割
class Solution:
    def __init__(self) -> None:
        self.result = []
        self.path = []
    
    # [start, end]
    def isValidIP(self, s: str, start: int, end: int) -> bool:
        if start > end:
            return False
        # if start with leading zeros.
        if s[start] == '0' and start != end:
            return False
        # if it contains nondigits.
        for i in range(start, end + 1):
            if not s[i].isdigit():
                return False
        num = int(s[start: end + 1])
        if num > 255:
            return False
        return True

    def backtracking(self, s: str, startIndex: int) -> None:
        # Return case.
        if len(self.path) == 4 and startIndex == len(s):
            self.result.append('.'.join(self.path))
            return

        if len(self.path) >= 4:
            return
        
        # Single layer logic.
        for i in range(startIndex, len(s)):
            print(startIndex, i)
            # print(len(s))
            if self.isValidIP(s, startIndex, i):
                sub = s[startIndex : i + 1]
                self.path.append(sub)
                print("append: ", self.path)
                self.backtracking(s, i + 1)
                self.path.pop()
                print("pop: ", self.path)
        return

    def restoreIpAddresses(self, s: str) -> List[str]:
        # Pruning
        if len(s) < 4 or len(s) > 12:
            return []
        self.result.clear()
        self.path.clear()
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
