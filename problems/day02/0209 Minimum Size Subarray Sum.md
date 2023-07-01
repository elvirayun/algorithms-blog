# 209. Minimum Size Subarray Sum

## Problem

*****

Given an array of positive integers `nums` and a positive integer `target`, return *the **minimal length** of a* 

*subarray*

 *whose sum is greater than or equal to* `target`. If there is no such subarray, return `0` instead.



**Example 1:**

```
Input: target = 7, nums = [2,3,1,2,4,3]
Output: 2
Explanation: The subarray [4,3] has the minimal length under the problem constraint.
```

**Example 2:**

```
Input: target = 4, nums = [1,4,4]
Output: 1
```

**Example 3:**

```
Input: target = 11, nums = [1,1,1,1,1,1,1,1]
Output: 0
```

 

**Constraints:**

- `1 <= target <= 109`
- `1 <= nums.length <= 105`
- `1 <= nums[i] <= 104`

 

**Follow up:** If you have figured out the `O(n)` solution, try coding another solution of which the time complexity is `O(n log(n))`.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 Sliding Window 双指针

### 1. Explanation

- 首先循环的指针是滑动窗口的右边界，right,  在窗口内的和小于target的时候，right就一直向右滑动。
- 直到窗口内的和 >= target, 此时开始向右滑动左指针来不断缩小滑动窗口的大小，以找到最小的窗口。
- 注意在滑动 left 的时候用的是`while`.

<img src="./0209%20Minimum%20Size%20Subarray%20Sum.assets/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303231303331323136303434313934322e706e67.png" alt="leetcode_209" style="zoom:67%;" />

可以发现**滑动窗口的精妙之处在于根据当前子序列和大小的情况，不断调节子序列的起始位置。从而将O(n^2)暴力解法降为O(n)。**



### 2. Important details

- 注意里面一层是``while`不是`for`。

- 以及left指针要移动， sum值也要修改。

### 3. Complexity

- Time complexity: `O(N)`
  - there is an inner while loop inside another for loop, isn't the time complexity `O(n^2)`? The reason it is still `O(n)` is because the right pointer `right` can move `n` times and the left pointer `left` can move also `n` times in total. The inner loop is not running `n` times for each iteration of the outer loop. A sliding window guarantees a maximum of `2n` window iterations. 

- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        # sliding window
        res = float('inf')
        left, right = 0, 0
        nums_length = len(nums)
        sum_of_current_window = 0

        for right in range(0, nums_length):
            sum_of_current_window += nums[right]

            while sum_of_current_window >= target:
                res = min(res, right - left + 1)
                sum_of_current_window -= nums[left]
                left += 1

        return res if res != float('inf') else 0
```



********

## Solution2 Brute Force

### 1. Explanation

- 直接用双层循环暴力求所有的和，然后找到最小值。

### 2. Important details

- 注意这里不是 `sum_of_current_window -= nums[left]` 了，而是每次移动left之后，sum归0重新求和。

### 3. Complexity

- Time complexity: `O(N^2)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def minSubArrayLen(self, target: int, nums: List[int]) -> int:
        nums_length = len(nums)
        res = float('inf')
        sum_of_current_window = 0

        for left in range(0, nums_length):
            sum_of_current_window = 0
            for right in range(left, nums_length):
                sum_of_current_window += nums[right]
                if sum_of_current_window >= target:
                    res = min(res, right - left + 1)
                    break

        return res if res != float('inf') else 0
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
