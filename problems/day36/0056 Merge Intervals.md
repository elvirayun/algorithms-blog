# [56. Merge Intervals](https://leetcode.com/problems/merge-intervals/)

## Problem

*****

Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return *an array of the non-overlapping intervals that cover all the intervals in the input*.

 

**Example 1:**

```
Input: intervals = [[1,3],[2,6],[8,10],[15,18]]
Output: [[1,6],[8,10],[15,18]]
Explanation: Since intervals [1,3] and [2,6] overlap, merge them into [1,6].
```

**Example 2:**

```
Input: intervals = [[1,4],[4,5]]
Output: [[1,5]]
Explanation: Intervals [1,4] and [4,5] are considered overlapping.
```

 

**Constraints:**

- `1 <= intervals.length <= 104`
- `intervals[i].length == 2`
- `0 <= starti <= endi <= 104`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 greedy

### 1. Explanation

- 还是重叠区间问题



### 2. Important details





### 3. Complexity

- Time complexity: `O(nlongn)`
- Space complexity: `O(logn)`, 排序需要的时间开销



### 4. Code

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if len(intervals) <= 1:
            return intervals
        # sort
        intervals.sort(key=lambda x: (x[0], x[1]))
        # 
        result = []
        result.append(intervals[0])
        for index in range(1, len(intervals)):
            curLeft, curRight = intervals[index][0], intervals[index][1]
            curPreRight = result[-1][1]
            if curLeft <= curPreRight:
                result[-1][1] = max(curPreRight, curRight)
            else:
                result.append(intervals[index])
        return result
```

- 详细注释版

```python
class Solution:
    def merge(self, intervals):
        result = []
        if len(intervals) == 0:
            return result  # 区间集合为空直接返回

        intervals.sort(key=lambda x: x[0])  # 按照区间的左边界进行排序

        result.append(intervals[0])  # 第一个区间可以直接放入结果集中

        for i in range(1, len(intervals)):
            if result[-1][1] >= intervals[i][0]:  # 发现重叠区间
                # 合并区间，只需要更新结果集最后一个区间的右边界，因为根据排序，左边界已经是最小的
                result[-1][1] = max(result[-1][1], intervals[i][1])
            else:
                result.append(intervals[i])  # 区间不重叠

        return result
```



********

## Solution2 自写解法

### 1. Explanation

-  自己第一遍写的解法，比较冗余
- Carl写的真的很精简，算法之美



### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def merge(self, intervals: List[List[int]]) -> List[List[int]]:
        if len(intervals) == 1:
            return intervals
        # sort
        intervals.sort(key=lambda x: (x[0], x[1]))
        left, right = intervals[0][0], intervals[0][1]
        result = []
        for index in range(1, len(intervals)):
            if intervals[index][0] <= right:
                left = min(left, intervals[index][0])
                right = max(right, intervals[index][1])
            else:
                result.append([left, right])
                left, right = intervals[index][0], intervals[index][1]
        # still there is a last interval needs to add.
        result.append([left, right])
        return result

```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
