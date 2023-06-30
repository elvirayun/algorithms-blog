# 27 Remove Element

## Problem

*****

Given an integer array `nums` and an integer `val`, remove all occurrences of `val` in `nums` [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm). The order of the elements may be changed. Then return *the number of elements in* `nums` *which are not equal to* `val`.

Consider the number of elements in `nums` which are not equal to `val` be `k`, to get accepted, you need to do the following things:

- Change the array `nums` such that the first `k` elements of `nums` contain the elements which are not equal to `val`. The remaining elements of `nums` are not important as well as the size of `nums`.
- Return `k`.

**Custom Judge:**

The judge will test your solution with the following code:

```
int[] nums = [...]; // Input array
int val = ...; // Value to remove
int[] expectedNums = [...]; // The expected answer with correct length.
                            // It is sorted with no values equaling val.

int k = removeElement(nums, val); // Calls your implementation

assert k == expectedNums.length;
sort(nums, 0, k); // Sort the first k elements of nums
for (int i = 0; i < actualLength; i++) {
    assert nums[i] == expectedNums[i];
}
```

If all assertions pass, then your solution will be **accepted**.

 

**Example 1:**

```
Input: nums = [3,2,2,3], val = 3
Output: 2, nums = [2,2,_,_]
Explanation: Your function should return k = 2, with the first two elements of nums being 2.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

**Example 2:**

```
Input: nums = [0,1,2,2,3,0,4,2], val = 2
Output: 5, nums = [0,1,4,0,3,_,_,_]
Explanation: Your function should return k = 5, with the first five elements of nums containing 0, 0, 1, 3, and 4.
Note that the five elements can be returned in any order.
It does not matter what you leave beyond the returned k (hence they are underscores).
```

 

**Constraints:**

- `0 <= nums.length <= 100`
- `0 <= nums[i] <= 50`
- `0 <= val <= 100`

******

### 1. Classification



### 2. Discussion



*******

## Solution1 双指针 Two pointers

### 1. Explanation

### 双指针法

库函数 `erase` / `remove` 的实现方式

双指针法（快慢指针法）： **通过一个快指针和慢指针在一个for循环下完成两个for循环的工作。**

定义快慢指针:

- 快指针：寻找新数组的元素 ，新数组就是不含有目标元素的数组
- 慢指针：指向更新 新数组下标的位置

![27.移除元素-双指针法](0027 Remove Element.assets/27.移除元素-双指针法.gif)

### 2. Important details

### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        fast_pointer, slow_pointer = 0, 0
        nums_length = len(nums)
        while fast_pointer < nums_length:
            if nums[fast_pointer] != val:
                nums[slow_pointer] = nums[fast_pointer]
                slow_pointer += 1
            fast_pointer += 1
        return slow_pointer
```

- Code with comments

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        # Two pointers
        # fast pointer finds elements that are not equal to val.
        # slow pointer records index.
        fast_pointer, slow_pointer = 0, 0
        nums_length = len(nums)
        while fast_pointer < nums_length:
            if nums[fast_pointer] != val:
                nums[slow_pointer] = nums[fast_pointer]
                slow_pointer += 1
            fast_pointer += 1
        # 最终slow_pointer的值刚好等于数组的长度
        return slow_pointer
```



********

## Solution2

### 1. Explanation

- 暴力的解法就是两层for循环，一个for循环遍历数组元素 ，第二个for循环更新数组。

![27.移除元素-暴力解法](0027%20Remove%20Element.assets/27.移除元素-暴力解法.gif)

### 2. Important details

- 注意移动完数组之后，`index` 需要 `-1` ，保证后面移动后的数组也会正常被遍历到。

### 3. Complexity

- Time complexity: `O(N^2)`
- Space complexity: `O(1)`

### 4. Code

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        index, nums_length = 0, len(nums)
        while index < nums_length:
            if nums[index] == val:
                for j_index in range(index + 1, nums_length):
                    nums[j_index - 1] = nums[j_index]
                index -= 1
                nums_length -= 1
            index += 1
        return index
```

- Code with comments

```python
class Solution:
    def removeElement(self, nums: List[int], val: int) -> int:
        # 暴力解法 brute force solution
        index, nums_length = 0, len(nums)
        while index < nums_length:
            if nums[index] == val:
                # 将后面的数组整体向前移动一格
                for j_index in range(index + 1, nums_length):
                    nums[j_index - 1] = nums[j_index]
                # 因为下标i以后的数值都向前移动了一位，所以i也向前移动一位
                index -= 1
                nums_length -= 1
            index += 1
        return index
```



## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
