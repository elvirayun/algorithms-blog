# [1005. Maximize Sum Of Array After K Negations](https://leetcode.com/problems/maximize-sum-of-array-after-k-negations/)

## Problem

*****

Given an integer array `nums` and an integer `k`, modify the array in the following way:

- choose an index `i` and replace `nums[i]` with `-nums[i]`.

You should apply this process exactly `k` times. You may choose the same index `i` multiple times.

Return *the largest possible sum of the array after modifying it in this way*.

 

**Example 1:**

```
Input: nums = [4,2,3], k = 1
Output: 5
Explanation: Choose index 1 and nums becomes [4,-2,3].
```

**Example 2:**

```
Input: nums = [3,-1,0,2], k = 3
Output: 6
Explanation: Choose indices (1, 2, 2) and nums becomes [3,1,0,2].
```

**Example 3:**

```
Input: nums = [2,-3,-1,5,-4], k = 2
Output: 13
Explanation: Choose indices (1, 4) and nums becomes [2,3,-1,5,4].
```

 

**Constraints:**

- `1 <= nums.length <= 104`
- `-100 <= nums[i] <= 100`
- `1 <= k <= 104`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 Greedy

### 1. Explanation

- 用绝对值排序就只需要排序一次
  - 原来有负数时按从小到大排序一次，没有负数时又需要从小到大排序一次（因为负数转正后可能会比原来的正数大）

****

- 两次贪心过程

贪心的思路，局部最优：让绝对值大的负数变为正数，当前数值达到最大，整体最优：整个数组和达到最大。

局部最优可以推出全局最优。

那么如果将负数都转变为正数了，K依然大于0，此时的问题是一个有序正整数序列，如何转变K次正负，让 数组和 达到最大。

那么又是一个贪心：局部最优：只找数值最小的正整数进行反转，当前数值和可以达到最大（例如正整数数组{5, 3, 1}，反转1 得到-1 比 反转5得到的-5 大多了），全局最优：整个 数组和 达到最大。

虽然这道题目大家做的时候，可能都不会去想什么贪心算法，一鼓作气，就AC了。

**我这里其实是为了给大家展现出来 经常被大家忽略的贪心思路，这么一道简单题，就用了两次贪心！**

那么本题的解题步骤为：

- 第一步：将数组按照绝对值大小从大到小排序，**注意要按照绝对值的大小**
- 第二步：从前向后遍历，遇到负数将其变为正数，同时K--
- 第三步：如果K还大于0，那么反复转变数值最小的元素，将K用完
- 第四步：求和

*****



**如果没有贪心的思考方式（局部最优，全局最优），很容易陷入贪心简单题凭感觉做，贪心难题直接不会做，其实这样就锻炼不了贪心的思考方式了**。

### 2. Important details

- 绝对值排序没想到
- 对最小值反复取反没想到

### 3. Complexity

- Time complexity:`O(NlogN)`, 排序的时间复杂度
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def largestSumAfterKNegations(self, nums: List[int], k: int) -> int:
        # 第一轮贪心
        # 绝对值排序从大到小排序
        nums.sort( key=lambda x: abs(x), reverse=True ) 
        # 
        for index in range(len(nums)):
            if nums[index] < 0 and k > 0:
                nums[index] *= -1
                k -= 1
        # 第二轮贪心
        # 根据剩余k的奇偶来判断第二轮最小值的正负
        if k % 2 == 1:
            nums[-1] *= -1
        
        result = sum(nums)
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
