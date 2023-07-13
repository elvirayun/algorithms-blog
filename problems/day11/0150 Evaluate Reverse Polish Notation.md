# 150. Evaluate Reverse Polish Notation

## Problem

*****

You are given an array of strings `tokens` that represents an arithmetic expression in a [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Evaluate the expression. Return *an integer that represents the value of the expression*.

**Note** that:

- The valid operators are `'+'`, `'-'`, `'*'`, and `'/'`.
- Each operand may be an integer or another expression.
- The division between two integers always **truncates toward zero**.
- There will not be any division by zero.
- The input represents a valid arithmetic expression in a reverse polish notation.
- The answer and all the intermediate calculations can be represented in a **32-bit**integer.

 

**Example 1:**

```
Input: tokens = ["2","1","+","3","*"]
Output: 9
Explanation: ((2 + 1) * 3) = 9
```

**Example 2:**

```
Input: tokens = ["4","13","5","/","+"]
Output: 6
Explanation: (4 + (13 / 5)) = 6
```

**Example 3:**

```
Input: tokens = ["10","6","9","3","+","-11","*","/","*","17","+","5","+"]
Output: 22
Explanation: ((10 * (6 / ((9 + 3) * -11))) + 17) + 5
= ((10 * (6 / (12 * -11))) + 17) + 5
= ((10 * (6 / -132)) + 17) + 5
= ((10 * 0) + 17) + 5
= (0 + 17) + 5
= 17 + 5
= 22
```

 

**Constraints:**

- `1 <= tokens.length <= 104`
- `tokens[i]` is either an operator: `"+"`, `"-"`, `"*"`, or `"/"`, or an integer in the range `[-200, 200]`.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- TODO：补充一些explanation

- 逆波兰表达式就是正常表达式的二叉树的后序遍历，计算机计算起来很方便

![150.逆波兰表达式求值](./0150%20Evaluate%20Reverse%20Polish%20Notation.assets/150.%E9%80%86%E6%B3%A2%E5%85%B0%E8%A1%A8%E8%BE%BE%E5%BC%8F%E6%B1%82%E5%80%BC.gif)



### 2. Important details

- 注意，数字要 int() 一下，把字符转成int.

### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`



### 4. Code

```python
class Solution:
    def evalRPN(self, tokens: List[str]) -> int:
        stack = []
        for token in tokens:
            if token == '+' or token == '-' or token == '*' or token == '/':
                num1 = int(stack.pop())
                num2 = int(stack.pop())
                if token == '+' : stack.append(num2 + num1)
                if token == '-' : stack.append(num2 - num1)
                if token == '*' : stack.append(num2 * num1)
                if token == '/' : stack.append(int(num2 / num1))
            else:
                token = int(token)
                stack.append(token)
        return stack.pop()
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
