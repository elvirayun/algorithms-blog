# 1. Two Sum

## Problem

*****

Given an array of integers `nums` and an integer `target`, return *indices of the two numbers such that they add up to `target`*.

You may assume that each input would have ***exactly\* one solution**, and you may not use the *same* element twice.

You can return the answer in any order.

 

**Example 1:**

```
Input: nums = [2,7,11,15], target = 9
Output: [0,1]
Explanation: Because nums[0] + nums[1] == 9, we return [0, 1].
```

**Example 2:**

```
Input: nums = [3,2,4], target = 6
Output: [1,2]
```

**Example 3:**

```
Input: nums = [3,3], target = 6
Output: [0,1]
```

 

**Constraints:**

- `2 <= nums.length <= 104`
- `-109 <= nums[i] <= 109`
- `-109 <= target <= 109`
- **Only one valid answer exists.**

 

**Follow-up:** Can you come up with an algorithm that is less than `O(n2) `time complexity?

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 使用 map / dict 作为hash map。

<img src="./0001%20Two%20Sum.assets/20220711202638.png" alt="过程一" style="zoom:50%;" />

<img src="./0001%20Two%20Sum.assets/20230220223536.png" alt="过程二" style="zoom:50%;" />

### 2. Important details

本题其实有四个重点：

- 为什么会想到用哈希表
- 哈希表为什么用map
- 本题map是用来存什么的
- map中的key和value用来存什么的

### 3. Complexity

- Time complexity: `O(N)` , 遍历数组一遍
- Space complexity: `O(N)` ， hash table 的存储空间。



### 4. Code

```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        # 使用python中的字典作为hash table, 相当于map
        hash_table = dict()
        
        for index, value in enumerate(nums):
            #  遍历当前元素，并在map中寻找是否有匹配的key
            if target - value in hash_table:
                return [hash_table[target - value], index]
            else:
                # 如果没找到匹配对，就把访问过的元素和下标加入到map中
                hash_table[value] = index
        
        return []
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
