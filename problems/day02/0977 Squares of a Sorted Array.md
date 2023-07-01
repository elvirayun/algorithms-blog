# 977 Squares of a Sorted Array

## Problem

*****

Given an integer array `nums` sorted in **non-decreasing** order, return *an array of **the squares of each number** sorted in non-decreasing order*.

**Example 1:**

```
Input: nums = [-4,-1,0,3,10]
Output: [0,1,9,16,100]
Explanation: After squaring, the array becomes [16,1,0,9,100].
After sorting, it becomes [0,1,9,16,100].
```

**Example 2:**

```
Input: nums = [-7,-3,2,3,11]
Output: [4,9,9,49,121]
```

**Constraints:**

- `1 <= nums.length <= 104`
- `-104 <= nums[i] <= 104`
- `nums` is sorted in **non-decreasing** order.

**Follow up:** Squaring each element and sorting the new array is very trivial, could you find an `O(n)` solution using a different approach?

******

### 1. Classification



### 2. Discussion





*******

## Solution1 Two pointers 双指针法

### 1. Explanation

数组其实是有序的， 只不过负数平方之后可能成为最大数了。

那么数组平方的最大值就在数组的两端，不是最左边就是最右边，不可能是中间。

此时可以考虑双指针法了，i指向起始位置，j指向终止位置。

定义一个新数组`result`，和A数组一样的大小，让k指向result数组终止位置。

<img src="./0977%20Squares%20of%20a%20Sorted%20Array.assets/68747470733a2f2f636f64652d7468696e6b696e672e63646e2e626365626f732e636f6d2f676966732f3937372e2545362539432538392545352542412538462545362539352542302545372542422538342545372539412538342545352542392542332545362539362542392e676966-20230629232727619.gif" alt="img" style="zoom:67%;" />

### 2. Important details

- 关键在于更新数组的时候直接由大到小更新即可，因为知道数组长度（**关键**!!）

- 比较的时候记的是`if abs(nums[left]) < abs(nums[right])` 而不是 `if abs(left) < abs(right)`

### 3. Complexity

- Time complexity: `0(N)`, 只遍历一遍。
- Space complexity: `O(N)`, 用了一个额外数组。

### 4. Code

```python
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        nums_length = len(nums)
        left, right = 0, nums_length - 1
        index = nums_length - 1
        result = [0] * nums_length
        while left <= right:
            if abs(nums[left]) < abs(nums[right]):
                result[index] = nums[right] ** 2
                right -= 1
            else:
                result[index] = nums[left] ** 2
                left += 1
            index -= 1
        return result
```



********

## Solution2 Brute Force

### 1. Explanation

Create an array of the squares of each element, and sort them.



### 2. Important details



### 3. Complexity

- Time Complexity: `O(Nlog⁡N)`, where N is the length of `nums`.
- Space complexity : `O(N)` or `O(log⁡N)`
  - The space complexity of the sorting algorithm depends on the implementation of each program language.
  - For instance, the `list.sort()` function in Python is implemented with the [Timsort](https://en.wikipedia.org/wiki/Timsort) algorithm whose space complexity is `O(N)`
  - In Java, the [Arrays.sort()](https://docs.oracle.com/javase/8/docs/api/java/util/Arrays.html#sort-byte:A-) is implemented as a variant of quicksort algorithm whose space complexity is `O(log⁡N)`. However, if the array is highly structured (has few sorted subarrays), then [linear space](https://github.com/openjdk/jdk/blob/jdk-14-ga/src/java.base/share/classes/java/util/DualPivotQuicksort.java#L733) may be used instead.

### 4. Code

```python
# 暴力排序法
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        for i in range(len(nums)):
            nums[i] *= nums[i]
        nums.sort()
        return nums
```

```python
# 暴力排序法+列表推导法
class Solution:
    def sortedSquares(self, nums: List[int]) -> List[int]:
        return sorted(x*x for x in nums)
```



## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
