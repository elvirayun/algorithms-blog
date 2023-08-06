# [37. Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)

## Problem

*****

Write a program to solve a Sudoku puzzle by filling the empty cells.

A sudoku solution must satisfy **all of the following rules**:

1. Each of the digits `1-9` must occur exactly once in each row.
2. Each of the digits `1-9` must occur exactly once in each column.
3. Each of the digits `1-9` must occur exactly once in each of the 9 `3x3` sub-boxes of the grid.

The `'.'` character indicates empty cells.

 

**Example 1:**

![img](./0037%20Sudoku%20Solver.assets/250px-Sudoku-by-L2G-20050714.svg.png)

```
Input: board = [["5","3",".",".","7",".",".",".","."],["6",".",".","1","9","5",".",".","."],[".","9","8",".",".",".",".","6","."],["8",".",".",".","6",".",".",".","3"],["4",".",".","8",".","3",".",".","1"],["7",".",".",".","2",".",".",".","6"],[".","6",".",".",".",".","2","8","."],[".",".",".","4","1","9",".",".","5"],[".",".",".",".","8",".",".","7","9"]]
Output: [["5","3","4","6","7","8","9","1","2"],["6","7","2","1","9","5","3","4","8"],["1","9","8","3","4","2","5","6","7"],["8","5","9","7","6","1","4","2","3"],["4","2","6","8","5","3","7","9","1"],["7","1","3","9","2","4","8","5","6"],["9","6","1","5","3","7","2","8","4"],["2","8","7","4","1","9","6","3","5"],["3","4","5","2","8","6","1","7","9"]]
Explanation: The input board is shown above and the only valid solution is shown below:
```

 

**Constraints:**

- `board.length == 9`
- `board[i].length == 9`
- `board[i][j]` is a digit or `'.'`.
- It is **guaranteed** that the input board has only one solution.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 二维递归

![37.解数独](./0037%20Sudoku%20Solver.assets/2020111720451790-20230310131816104.png)



### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def solveSudoku(self, board: List[List[str]]) -> None:
        """
        Do not return anything, modify board in-place instead.
        """
        self.backtracking(board)

    def backtracking(self, board: List[List[str]]) -> bool:
        # 有解返回True, 无解返回False.
        # 二维递归
        for row in range(len(board)):
            for col in range(len(board[0])):
                # 寻找空格
                if board[row][col] != '.':
                    continue
                for k in range(1, 10):
                    if self.isValid(row, col, k, board):
                        board[row][col] = str(k)
                        if self.backtracking(board):
                            return True
                        board[row][col] = '.'
                return False
        return True

    def isValid(self, row: int, col: int, k: int, board: List[List[str]]) -> bool:
        # 判断同一行
        for j in range(9):
            if board[row][j] == str(k):
                return False
        # 判断同一列
        for i in range(9):
            if board[i][col] == str(k):
                return False
        # 判断九宫格
        # 这一步真的绝
        startRow = ( row // 3 ) * 3
        startCol = ( col // 3 ) * 3
        for row2 in range(startRow, startRow + 3):
            for col2 in range(startCol, startCol + 3):
                if board[row2][col2] == str(k):
                    return False
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
