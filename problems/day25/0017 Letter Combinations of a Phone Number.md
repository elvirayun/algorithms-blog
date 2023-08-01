# 17. Letter Combinations of a Phone Number

## Problem

*****

Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

<img src="./0017%20Letter%20Combinations%20of%20a%20Phone%20Number.assets/1200px-telephone-keypad2svg.png" alt="img" style="zoom:50%;" />

 

**Example 1:**

```
Input: digits = "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**Example 2:**

```
Input: digits = ""
Output: []
```

**Example 3:**

```
Input: digits = "2"
Output: ["a","b","c"]
```

 

**Constraints:**

- `0 <= digits.length <= 4`
- `digits[i]` is a digit in the range `['2', '9']`.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 回溯

### 1. Explanation

- 思路和0077 Combination 与 0216 Combination Sum II 类似



### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        self.dict = {
            "2":"abc",
            "3":"def",
            "4":"ghi",
            "5":"jkl",
            "6":"mno",
            "7":"pqrs",
            "8":"tuv",
            "9":"wxyz"
        }
        self.path = []
        self.result = []
    
    def backtracking(self, digits:str, startIndex: int) -> None:
        # return case.
        if startIndex == len(digits):
            if self.path:
                result_str = ''.join(self.path)
                self.result.append(result_str)
            return
        # Single layer.
        for char in self.dict.get(digits[startIndex]):
            self.path.append(char)
            self.backtracking(digits, startIndex + 1)
            self.path.pop()
        return

    def letterCombinations(self, digits: str) -> List[str]:
        self.backtracking(digits, 0)
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
