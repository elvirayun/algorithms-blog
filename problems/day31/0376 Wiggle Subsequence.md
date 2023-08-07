# [376. Wiggle Subsequence](https://leetcode.com/problems/wiggle-subsequence/)

## Problem

*****

A **wiggle sequence** is a sequence where the differences between successive numbers strictly alternate between positive and negative. The first difference (if one exists) may be either positive or negative. A sequence with one element and a sequence with two non-equal elements are trivially wiggle sequences.

- For example, `[1, 7, 4, 9, 2, 5]` is a **wiggle sequence** because the differences `(6, -3, 5, -7, 3)` alternate between positive and negative.
- In contrast, `[1, 4, 7, 2, 5]` and `[1, 7, 4, 5, 5]` are not wiggle sequences. The first is not because its first two differences are positive, and the second is not because its last difference is zero.

A **subsequence** is obtained by deleting some elements (possibly zero) from the original sequence, leaving the remaining elements in their original order.

Given an integer array `nums`, return *the length of the longest **wiggle subsequence** of* `nums`.

  

**Example 1:**

```
Input: nums = [1,7,4,9,2,5]
Output: 6
Explanation: The entire sequence is a wiggle sequence with differences (6, -3, 5, -7, 3).
```

**Example 2:**

```
Input: nums = [1,17,5,10,13,15,10,5,16,8]
Output: 7
Explanation: There are several subsequences that achieve this length.
One is [1, 17, 10, 13, 10, 16, 8] with differences (16, -7, 3, -3, 6, -8).
```

**Example 3:**

```
Input: nums = [1,2,3,4,5,6,7,8,9]
Output: 2
```

 

**Constraints:**

- `1 <= nums.length <= 1000`
- `0 <= nums[i] <= 1000`

 

**Follow up:** Could you solve this in `O(n)` time?

******

### 1. Classification



### 2. Discussion





*******

## Solution1 贪心解法

### 1. Explanation

![376.摆动序列](./0376%20Wiggle%20Subsequence.assets/20201124174327597.png)



**局部最优：删除单调坡度上的节点（不包括单调坡度两端的节点），那么这个坡度就可以有两个局部峰值**。

**整体最优：整个序列有最多的局部峰值，从而达到最长摆动序列**。

这是我们思考本题的一个大题思路，但本题要考虑三种情况：

1. 情况一：上下坡中有平坡
2. 情况二：数组首尾两端
3. 情况三：单调坡中有平坡

![img](./0376%20Wiggle%20Subsequence.assets/20230106172613.png)

![img](./0376%20Wiggle%20Subsequence.assets/20230108171505.png)

![IMG_0637](./0376%20Wiggle%20Subsequence.assets/IMG_0637.jpeg)



### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def wiggleMaxLength(self, nums: List[int]) -> int:
        if len(nums) == 0:
            return 1
        # 当前元素和它后面的元素的差值
        curDiff = 0
        # 前一个差值, 默认第一个元素的前一个差值是0
        preDiff = 0
        # 总共的坡度值，默认为1，因为默认最后一个值（最右值是一个坡度）
        result = 1
        # 遍历到倒数第二个值
        for index in range(len(nums) - 1):
            curDiff = nums[index + 1] - nums[index]
            if preDiff <= 0 and curDiff > 0 or preDiff >= 0 and curDiff < 0:
                result += 1
                # 只在有摆动的时候移动preDiff.(考虑到单调平坡的情况)
                preDiff = curDiff
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
