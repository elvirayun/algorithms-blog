# 20. Valid Parentheses

## Problem

*****

Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.

 

**Example 1:**

```
Input: s = "()"
Output: true
```

**Example 2:**

```
Input: s = "()[]{}"
Output: true
```

**Example 3:**

```
Input: s = "(]"
Output: false
```

 

**Constraints:**

- `1 <= s.length <= 104`
- `s` consists of parentheses only `'()[]{}'`.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- [题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0020.%E6%9C%89%E6%95%88%E7%9A%84%E6%8B%AC%E5%8F%B7.md)

1. 第一种情况，字符串里左方向的括号多余了 ，所以不匹配。 ![括号匹配1](https://code-thinking-1253855093.file.myqcloud.com/pics/2020080915505387.png)
2. 第二种情况，括号没有多余，但是 括号的类型没有匹配上。 ![括号匹配2](https://code-thinking-1253855093.file.myqcloud.com/pics/20200809155107397.png)
3. 第三种情况，字符串里右方向的括号多余了，所以不匹配。 ![括号匹配3](./0020%20Valid%20Parentheses.assets/20200809155115779.png)

我们的代码只要覆盖了这三种不匹配的情况，就不会出问题，可以看出 动手之前分析好题目的重要性。

动画如下：

![20.有效括号](./0020%20Valid%20Parentheses.assets/20.%E6%9C%89%E6%95%88%E6%8B%AC%E5%8F%B7.gif)

第一种情况：已经遍历完了字符串，但是栈不为空，说明有相应的左括号没有右括号来匹配，所以return false

第二种情况：遍历字符串匹配的过程中，发现栈里没有要匹配的字符。所以return false

第三种情况：遍历字符串匹配的过程中，栈已经为空了，没有匹配的字符了，说明右括号没有找到对应的左括号return false

那么什么时候说明左括号和右括号全都匹配了呢，就是字符串遍历完之后，栈是空的，就说明全都匹配了。

分析完之后，代码其实就比较好写了，

但还有一些技巧，在匹配左括号的时候，右括号先入栈，就只需要比较当前元素和栈顶相不相等就可以了，比左括号先入栈代码实现要简单的多了！



### 2. Important details

- **在匹配左括号的时候，右括号先入栈，就只需要比较当前元素和栈顶相不相等就可以了，比左括号先入栈代码实现要简单的多了！**

### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`



### 4. Code

```python
class Solution:
    def isValid(self, s: str) -> bool:
        # 剪枝 - 如果len(s)为偶数, 则不可能是valid parentheses
        if len(s) % 2 != 0 : return False

        stack = []
        for char in s:
            if char == '(' : stack.append(')')
            elif char == '{' : stack.append('}')
            elif char == '[' : stack.append(']')
            elif len(stack) == 0 or char != stack[-1]:
                return False
            else:
                stack.pop()
        
        return True if len(stack) == 0 else False

# 1. 此时 len(stack) == 0 说明少了左括号
# 2. char != stack[-1] 说明左右括号不匹配
# 3. 如果结束后len(stack)不为0说明 左括号多了
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
