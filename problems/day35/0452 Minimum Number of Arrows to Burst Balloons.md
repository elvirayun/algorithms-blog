# [452. Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)

## Problem

*****

There are some spherical balloons taped onto a flat wall that represents the XY-plane. The balloons are represented as a 2D integer array `points` where `points[i] = [xstart, xend]` denotes a balloon whose **horizontal diameter** stretches between `xstart` and `xend`. You do not know the exact y-coordinates of the balloons.

Arrows can be shot up **directly vertically** (in the positive y-direction) from different points along the x-axis. A balloon with `xstart` and `xend` is **burst** by an arrow shot at `x` if `xstart <= x <= xend`. There is **no limit** to the number of arrows that can be shot. A shot arrow keeps traveling up infinitely, bursting any balloons in its path.

Given the array `points`, return *the **minimum** number of arrows that must be shot to burst all balloons*.

 

**Example 1:**

```
Input: points = [[10,16],[2,8],[1,6],[7,12]]
Output: 2
Explanation: The balloons can be burst by 2 arrows:
- Shoot an arrow at x = 6, bursting the balloons [2,8] and [1,6].
- Shoot an arrow at x = 11, bursting the balloons [10,16] and [7,12].
```

**Example 2:**

```
Input: points = [[1,2],[3,4],[5,6],[7,8]]
Output: 4
Explanation: One arrow needs to be shot for each balloon for a total of 4 arrows.
```

**Example 3:**

```
Input: points = [[1,2],[2,3],[3,4],[4,5]]
Output: 2
Explanation: The balloons can be burst by 2 arrows:
- Shoot an arrow at x = 2, bursting the balloons [1,2] and [2,3].
- Shoot an arrow at x = 4, bursting the balloons [3,4] and [4,5].
```

 

**Constraints:**

- `1 <= points.length <= 105`
- `points[i].length == 2`
- `-231 <= xstart < xend <= 231 - 1`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

**为了让气球尽可能的重叠，需要对数组进行排序**。

**如果气球重叠了，重叠气球中右边边界的最小值 之前的区间一定需要一个弓箭**。

![452.用最少数量的箭引爆气球](./0452%20Minimum%20Number%20of%20Arrows%20to%20Burst%20Balloons.assets/20201123101929791.png)



### 2. Important details

这道题目贪心的思路很简单也很直接，就是重复的一起射了。

而且寻找重复的气球，寻找重叠气球最小右边界，其实都有代码技巧。

贪心题目有时候就是这样，看起来很简单，思路很直接，但是一写代码就感觉贼复杂无从下手。



### 3. Complexity

- Time complexity: `O(NlogN)`, 排序算法时间复杂度
- Space complexity: `O(logn)`, Python 中的 Timsort 的时间复杂度



### 4. Code

- 详细注释

```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        # 好多题写完可以去写游戏了, 比如本题
        # 先按照左边界排序
        points.sort(key=lambda x: x[0])
        if len(points) <= 1:
            return len(points)
        # 射箭数初始化为1
        result = 1
        # 从第一位开始遍历
        for index in range(1, len(points)):
            # 当前左边界大于前一个的右边界
            if points[index][0] > points[index - 1][1]:
                result += 1
            # 当边界等于的时候也算重叠
            else:
                # 更新右边界为最小右边界
                points[index][1] = min(points[index - 1][1], points[index][1])
        return result
```

- 省略注释版

```python
class Solution:
    def findMinArrowShots(self, points: List[List[int]]) -> int:
        points.sort(key=lambda x: x[0])
        if len(points) <= 1:
            return len(points)
        result = 1
        for index in range(1, len(points)):
            if points[index][0] > points[index - 1][1]:
                result += 1
            else:
                points[index][1] = min(points[index - 1][1], points[index][1])
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
