# [435. Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)

## Problem

*****

Given an array of intervals `intervals` where `intervals[i] = [starti, endi]`, return *the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping*.

 

**Example 1:**

```
Input: intervals = [[1,2],[2,3],[3,4],[1,3]]
Output: 1
Explanation: [1,3] can be removed and the rest of the intervals are non-overlapping.
```

**Example 2:**

```
Input: intervals = [[1,2],[1,2],[1,2]]
Output: 2
Explanation: You need to remove two [1,2] to make the rest of the intervals non-overlapping.
```

**Example 3:**

```
Input: intervals = [[1,2],[2,3]]
Output: 0
Explanation: You don't need to remove any of the intervals since they're already non-overlapping.
```

 

**Constraints:**

- `1 <= intervals.length <= 105`
- `intervals[i].length == 2`
- `-5 * 104 <= starti < endi <= 5 * 104`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 和 [0452 Minimum Number of Arrows to Burst Balloons](../day35/0452%20Minimum%20Number%20of%20Arrows%20to%20Burst%20Balloons.md) 类似
- 找到重复后更新为最小的右边界


### 2. Important details





### 3. Complexity

- Time complexity: `O(NlogN)`
- Space complexity: `O(1)`

 

### 4. Code

```python
class Solution:
    def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
        if len(intervals) <= 1:
            return 0
        # 先排序
        intervals.sort(key=lambda x: x[0])
        result = 0
        # 再查找重叠区间
        for index in range(1, len(intervals)):
            if intervals[index][0] < intervals[index - 1][1]:
                result += 1
                # 更新interval，保留较小右边界，这样才能最大化保证后面不重叠
                intervals[index][1] = min(intervals[index][1], intervals[index - 1][1])
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
