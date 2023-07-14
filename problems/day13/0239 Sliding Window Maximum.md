# 239. Sliding Window Maximum

## Problem

*****

You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.

Return *the max sliding window*.

 

**Example 1:**

```
Input: nums = [1,3,-1,-3,5,3,6,7], k = 3
Output: [3,3,5,5,6,7]
Explanation: 
Window position                Max
---------------               -----
[1  3  -1] -3  5  3  6  7       3
 1 [3  -1  -3] 5  3  6  7       3
 1  3 [-1  -3  5] 3  6  7       5
 1  3  -1 [-3  5  3] 6  7       5
 1  3  -1  -3 [5  3  6] 7       6
 1  3  -1  -3  5 [3  6  7]      7
```

**Example 2:**

```
Input: nums = [1], k = 1
Output: [1]
```

 

**Constraints:**

- `1 <= nums.length <= 105`
- `-104 <= nums[i] <= 104`
- `1 <= k <= nums.length`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 需要自己构建单调队列

### 1. Explanation

- [题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0239.%E6%BB%91%E5%8A%A8%E7%AA%97%E5%8F%A3%E6%9C%80%E5%A4%A7%E5%80%BC.md)

  ![239.滑动窗口最大值-2](./0239%20Sliding%20Window%20Maximum.assets/68747470733a2f2f636f64652d7468696e6b696e672e63646e2e626365626f732e636f6d2f676966732f3233392e2545362542422539312545352538412541382545372541412539372545352538462541332545362539432538302545352541342541372545352538302542432d322e676966.gif)



- 需要自己构建单调队列
  - `push()`: 作用是保持当前窗口的最大值始终保持在第一位。
    - 所以当push当前窗口的所有值时，每当push一个值就和已经在队列里的所有值比较
    - 如果队列里面的值小于当前想要push的值，就把在队列里的值弹出，`queue.pop()`
    - 直接从尾部弹出
    - 这样操作下来可以保证队列里面的值始终是单调递减的，并且最大值始终在第一位
  - `pop()`: 只有在需要pop的值时当前的第一位时才会真正执行pop操作。
  - `getMaxValue`: 当前队列的第一位



- 所以主函数的逻辑
  - 把前k个直接push进自定义queue.
  - 从第k + 1 个开始，
    - 开始滑动窗口
    - Pop掉最前面的那一个值
    - Push新加入的值
    - 使用getMaxValue获得当前窗口最大值



### 2. Important details

- 在pop函数中，是`while ` 不是`if`: 如果一直小于将要push的值的话，要一直删掉小值

- 记住如果是坐标i/index的话，获取值一定要记得加 数组名！`nums[i]`

  

### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(K)`, K 是窗口大小，也是自定义单调queue的空间



### 4. Code

```python
from collections import deque

# 单调队列 - 单调递减队列
class MyQueue:
    def __init__(self) -> None:
        self.queue = deque()
    
    def pop(self, value: int) -> None:
        if self.queue and value == self.queue[0]:
            self.queue.popleft()

    def push(self, value: int) -> None:
        # 这里value不能等于self.queue[-1], 因为如果是相等的值的话
        # 都要保留
        while self.queue and value > self.queue[-1]:
            self.queue.pop()
        self.queue.append(value)

    def getMaxValue(self) -> int:
        return self.queue[0]

class Solution:
    def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
        queue = MyQueue()
        result = []
        for i in range(k):
            queue.push(nums[i])
        result.append(queue.getMaxValue())
        for i in range(k, len(nums)):
            queue.pop(nums[i - k])
            queue.push(nums[i])
            result.append(queue.getMaxValue())
        return result
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
