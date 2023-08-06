# [51. N-Queens](https://leetcode.com/problems/n-queens/)

## Problem

*****

The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return *all distinct solutions to the **n-queens puzzle***. You may return the answer in **any order**.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.

 

**Example 1:**

![img](./0051%20N-Queens.assets/queens.jpg)

```
Input: n = 4
Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
Explanation: There exist two distinct solutions to the 4-queens puzzle as shown above
```

**Example 2:**

```
Input: n = 1
Output: [["Q"]]
```

 

**Constraints:**

- `1 <= n <= 9`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 回溯算法的时间复杂度和嵌套for循环的时间复杂度相同
- 回溯相当于是用递归来控制for循环的层数


![img|500](./0051%20N-Queens.assets/20210130182532303-20230310122134167.jpg)

### 2. Important details

- 写代码的时候注意细节

- 比如 i 和 j 设置清楚

  



### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        self.result = []
        self.chessboard = []

    def solveNQueens(self, n: int) -> List[List[str]]:
        # 二维数组
        self.chessboard = [['.'] * n for _ in range(n)]
        self.backtracking(n, 0)
        return self.result

    def backtracking(self, n: int, row: int) -> None:
        if row == n:
            tmp = []
            for i in range(n):
                tmp.append(''.join(self.chessboard[i]))
            self.result.append(tmp[:])
            return
        # Current layer.
        for col in range(n):
            if self.isValid(row, col, n):
                self.chessboard[row][col] = 'Q'
                self.backtracking(n, row + 1)
                self.chessboard[row][col] = '.'
        return
    
    def isValid(self, row: int, col: int, n:int):
        # 不用检查行
        # 检查列
        for i in range(row):
            if self.chessboard[i][col] == 'Q':
                return False
        # 检查右上
        i, j = row - 1, col + 1
        while i >= 0 and j >= 0 and j < n:
            if self.chessboard[i][j] == 'Q':
                return False
            i -= 1
            j += 1
        # 检查左上
        i, j = row - 1, col - 1
        while i >= 0 and j >= 0:
            if self.chessboard[i][j] == 'Q':
                return False
            i -= 1
            j -= 1
        # 
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
