# 59. Spiral Matrix II

## Problem

*****

Given a positive integer `n`, generate an `n x n` `matrix` filled with elements from `1` to `n2` in spiral order.

**Example 1:**

![img](./0059%20Spiral%20Matrix%20II.assets/spiraln.jpg)

```
Input: n = 3
Output: [[1,2,3],[8,9,4],[7,6,5]]
```

**Example 2:**

```
Input: n = 1
Output: [[1]]
```

 

**Constraints:**

- `1 <= n <= 20`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 关键是保证**循环不变量**，无论哪条边都保持“**左闭右开**” `[ )`s

<img src="./0059%20Spiral%20Matrix%20II.assets/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303232303932323130323233362e706e67.png" alt="img" style="zoom: 33%;" />



### 2. Important details

- 旋转层数为 n // 2
- 当n为奇数时，中间点也是 n // 2

### 3. Complexity

- Time complexity: `O(N^2)` ，模拟遍历二维矩阵的时间
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def generateMatrix(self, n: int) -> List[List[int]]:
        nums = [[0] * n for _ in range(n)]
        start_row, start_col = 0, 0              # 起始点
        layer, middle = n // 2, n // 2           # 旋转层数，和当n为奇数时的中间点
        count = 1                                # 记数

        for offset in range(1, layer + 1):       # offset 逐层递增，从1开始
            for col in range(start_col, n - offset):     # from left to right
                nums[start_row][col] = count
                count += 1
            for row in range(start_row, n - offset):     # from top to bottom
                nums[row][n - offset] = count
                count += 1
            for col in range(n - offset, start_col, -1): # from right to left
                nums[n - offset][col] = count
                count += 1
            for row in range(n - offset, start_row, -1): # from bottom to top
                nums[row][start_col] = count
                count += 1
            start_row += 1                               # rememenber to updat start_row and start_col 
            start_col += 1
        
        if n % 2 != 0:
            nums[middle][middle] = count
        
        return nums
```



## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
