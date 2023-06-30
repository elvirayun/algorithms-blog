# 704 Binary Search

## Problem

****

Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.

**Example 1:**

```
Input: nums = [-1,0,3,5,9,12], target = 9
Output: 4
Explanation: 9 exists in nums and its index is 4
```

**Example 2:**

```
Input: nums = [-1,0,3,5,9,12], target = 2
Output: -1
Explanation: 2 does not exist in nums so return -1
```

**Constraints:**

- `1 <= nums.length <= 104`
- `-104 < nums[i], target < 104`
- All the integers in `nums` are **unique**.
- `nums` is sorted in ascending order.

****

### 1. Classification



### 2. Discussion

朴素二分法

**这道题目的前提是数组为有序数组**，同时题目还强调**数组中无重复元素**，因为一旦有重复元素，使用二分查找法返回的元素下标可能不是唯一的，这些都是使用二分法的前提条件，当大家看到题目描述满足如上条件的时候，可要想一想是不是可以用二分法了。

*****



## Solution1: 左闭右闭 closed interval (主要记这个方法)

### 1. Explanation

### 2. Important details

- `right = len(nums) - 1`

- Python `/` and `//`

- `while left <= right:`

- `right = middle - 1`

   

#### 2.1 Python `/` and `//`

在 Python 中, `/` 和 `//` 这两个符号都是用来做除法的，但是他们的行为方式稍有不同。

- `/` 是传统的除法。它会返回一个浮点数（即，带有小数的数），无论被除数和除数是否都是整数。例如 `5 / 2` 会返回 `2.5`。
- `//` 是地板除法。如果被除数和除数都是整数，它会返回商的整数部分，丢弃余数。例如 `5 // 2` 会返回 `2`。但是，如果其中至少有一个数是浮点数，那么结果也会是浮点数，但仍然会向下取整。例如 `5.0 // 2` 会返回 `2.0`。

这些规则适用于 Python 2.2 及之后的版本。在 Python 2.2 之前，`/` 的行为更像 `//`，即总是执行地板除法，除非至少有一个操作数是浮点数。从 Python 3.0 开始，`/` 的行为改变为总是执行浮点除法，而 `//` 用于地板除法

### 3. Complexity

- Time Complexity: `O(logn)` 二分查找 `O(logn)`

- Space Complexity: `O(1)`

### 4. Code

- Code

  ```python
  class Solution:
      def search(self, nums: List[int], target: int) -> int:
          # closed interval []
          left, right = 0, len(nums) - 1
          while left <= right:
              middle = left + (right - left) // 2
              if target == nums[middle]:
                  return middle
              elif target < nums[middle]:
                  right = middle - 1
              else:
                  left = middle + 1
          return -1
  ```

  

- Code with more comments

  ```python
  class Solution:
      def search(self, nums: List[int], target: int) -> int:
          # binary search
          # remember here is len(nums) - 1
          left, right = 0, len(nums) - 1
          # closed interval []
          while left <= right:
              # python / and //
              # Use // here, Floor Division operator.
            	# prevent overflow  
              middle = left + (right - left) // 2
              # print("middle:", middle)
              # narrow the interval
              if target == nums[middle]:
                  # print("middle:", middle)
                  return middle
              elif target < nums[middle]:
                  right = middle - 1
              else:
                  left = middle + 1
          return -1
  ```

  

********

## Solution2: 左闭右开 left-closed right-open interval

### 1. Explanation

### 2. Important details

- `right = len(nums)`
- `while left < right`
- `right = middle`

### 3. Complexity

- Time Complexity: `O(logn)` 二分查找 `O(logn)`

- Space Complexity: `O(1)`

### 4. Code

```python
class Solution:
    def search(self, nums: List[int], target: int) -> int:
        # left-closed and right-open interval [)
        left, right = 0, len(nums)
        while left < right:
            middle = left + (right - left) // 2
            if target == nums[middle]:
                return middle
            elif target < nums[middle]:
                right = middle
            else:
                left = middle + 1
        return -1
```



## References

- [代码随想录](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)



