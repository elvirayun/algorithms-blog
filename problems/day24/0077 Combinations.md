# 77. Combinations

## Problem

*****

Given two integers `n` and `k`, return *all possible combinations of* `k` *numbers chosen from the range* `[1, n]`.

You may return the answer in **any order**.

 

**Example 1:**

```
Input: n = 4, k = 2
Output: [[1,2],[1,3],[1,4],[2,3],[2,4],[3,4]]
Explanation: There are 4 choose 2 = 6 total combinations.
Note that combinations are unordered, i.e., [1,2] and [2,1] are considered to be the same combination.
```

**Example 2:**

```
Input: n = 1, k = 1
Output: [[1]]
Explanation: There is 1 choose 1 = 1 total combination.
```

 

**Constraints:**

- `1 <= n <= 20`
- `1 <= k <= n`

******

### 1. Classification



### 2. Discussion





*******

## Solution1回溯算法·不剪枝

### 1. Explanation

回溯算法模版

```python
void backtracking(参数) {
    if (终止条件) {
        存放结果;
        return;
    }

    for (选择：本层集合中元素（树中节点孩子的数量就是集合的大小）) {
        处理节点;
        backtracking(路径，选择列表); // 递归
        回溯，撤销处理结果
    }
}
```





![77.组合](./0077%20Combinations.assets/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303230313132333139353232333934302e706e67.png)



### 2. Important details



- 注意细节python中 list 的深拷贝是 a = b[:]

- self.result.append(self.path[:])

### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        # path and result.
        self.path = []
        self.result = []
    
    def backtracking(self, n: int, k:int, startIndex: int) -> None:
        # Return case -> collect results.
        if len(self.path) == k:
            self.result.append(self.path[:])
            return
        # Single layer logic
        # n -> [0,1,2,3,...n]
        for i in range(startIndex, n + 1):
            self.path.append(i)
            self.backtracking(n, k, i + 1)
            self.path.pop()
        return
        
    def combine(self, n: int, k: int) -> List[List[int]]:
        self.backtracking(n, k, 1)
        return self.result
```



********

## Solution2 回溯算法 剪枝

### 1. Explanation

- 根据len(path)剪枝，比如求k == 4的组合，那么长度为3的组合长度明显可以剪枝掉
- 剪枝公式  `n - (k - len(self.path) + 1)`
-  后面又加了一个1是因为range的左闭右开原则

```python
    # 剪枝 range(startIndex, n + 1) -> 
    # range(startIndex, n - (k-len(self.path)+1 +1)
```

<img src="./0077%20Combinations.assets/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303231303133303139343333353230372e706e67.png" alt="77.组合4" style="zoom:50%;" />



### 2. Important details



### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def __init__(self) -> None:
        # path and result.
        self.path = []
        self.result = []
    
    def backtracking(self, n: int, k:int, startIndex: int) -> None:
        # Return case -> collect results.
        if len(self.path) == k:
            self.result.append(self.path[:])
            return
        # Single layer logic
        # n -> [0,1,2,3,...n]
        # 剪枝 range(startIndex, n + 1) -> 
        # range(startIndex, n - (k-len(self.path)+1 +1)
        for i in range(startIndex, n - (k - len(self.path)) + 2):
            self.path.append(i)
            self.backtracking(n, k, i + 1)
            self.path.pop()
        return
        
    def combine(self, n: int, k: int) -> List[List[int]]:
        self.backtracking(n, k, 1)
        return self.result
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
