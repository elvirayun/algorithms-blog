# [53. Maximum Subarray](https://leetcode.com/problems/maximum-subarray/)

## Problem

*****

Given an integer array `nums`, find the 

subarray

 with the largest sum, and return *its sum*.

 

**Example 1:**

```
Input: nums = [-2,1,-3,4,-1,2,1,-5,4]
Output: 6
Explanation: The subarray [4,-1,2,1] has the largest sum 6.
```

**Example 2:**

```
Input: nums = [1]
Output: 1
Explanation: The subarray [1] has the largest sum 1.
```

**Example 3:**

```
Input: nums = [5,4,-1,7,8]
Output: 23
Explanation: The subarray [5,4,-1,7,8] has the largest sum 23.
```

 

**Constraints:**

- `1 <= nums.length <= 105`
- `-104 <= nums[i] <= 104`

 

**Follow up:** If you have figured out the `O(n)` solution, try coding another solution using the **divide and conquer** approach, which is more subtle.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 Brute force

### 1. Explanation

- 两层 For 循环



### 2. Important details





### 3. Complexity

- Time complexity: `O(N^2)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        # brute force solution.
        # double for loop.
        maxSum = float('-inf')
        curSum = 0
        # left and right index.
        # left -> startIndex.
        for left in range(len(nums)):
            curSum = 0
            # right -> endIndex.
            for right in range(left, len(nums)):
                curSum += nums[right]
                maxSum = max(curSum, maxSum)
        return maxSum
```



********

## Solution2 Greedy

### 1. Explanation

- 局部最优

  ```
  curSum += nums[index]
  ```

  如果当前和小于0，直接抛弃当前和，直接从下一个数开始重新计算.

  - 负数1 + 负数2 < 负数2
  - 负数1 + 正数2 < 正数2



### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`

 

### 4. Code

```python
class Solution:
    def maxSubArray(self, nums: List[int]) -> int:
        # greedy
        maxSum = float('-inf')
        curSum = 0
        for index in range(len(nums)):
            curSum += nums[index]
            maxSum = max(curSum, maxSum)
            if curSum < 0:
                curSum = 0
        return maxSum
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
