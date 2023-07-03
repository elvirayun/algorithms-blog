# 202. Happy Number

## Problem

*****

Write an algorithm to determine if a number `n` is happy.

A **happy number** is a number defined by the following process:

- Starting with any positive integer, replace the number by the sum of the squares of its digits.
- Repeat the process until the number equals 1 (where it will stay), or it **loops endlessly in a cycle** which does not include 1.
- Those numbers for which this process **ends in 1** are happy.

Return `true` *if* `n` *is a happy number, and* `false` *if not*.

 

**Example 1:**

```
Input: n = 19
Output: true
Explanation:
12 + 92 = 82
82 + 22 = 68
62 + 82 = 100
12 + 02 + 02 = 1
```

**Example 2:**

```
Input: n = 2
Output: false
```

 

**Constraints:**

- `1 <= n <= 231 - 1`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- [Leetcode.cn题解 - 优质](https://leetcode.cn/problems/happy-number/solution/kuai-le-shu-by-leetcode-solution/)
  - Hash table 
  - 快慢指针法
  - 数学法

### 2. Important details

### 3. Complexity

假设获得结果需要x步

- Time complexity: `O(x)`
- Space complexity: `O(x)`



### 4. Code

- 使用set hash table查找是否出现了重复的数

```python
class Solution:
    def isHappy(self, n: int) -> bool:
        record  = set()
        
        while n != 1:
            if n not in record:
                record.add(n)
                n = self.get_sum(n)
            else:
                # 重复了说明不是快乐数
                return False
        # 出了循环说明 n == 1, 是快乐数
        return True
    

    def get_sum(self, n: int) -> int:
        new_int = 0
        while n:
            n, r = divmod(n, 10)
            new_int += r ** 2
        return new_int
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
