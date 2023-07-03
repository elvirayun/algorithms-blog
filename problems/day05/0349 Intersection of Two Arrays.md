# 349. Intersection of Two Arrays

## Problem

*****

Given two integer arrays `nums1` and `nums2`, return *an array of their intersection*. Each element in the result must be **unique** and you may return the result in **any order**.

 

**Example 1:**

```
Input: nums1 = [1,2,2,1], nums2 = [2,2]
Output: [2]
```

**Example 2:**

```
Input: nums1 = [4,9,5], nums2 = [9,4,9,8,4]
Output: [9,4]
Explanation: [4,9] is also accepted.
```

 

**Constraints:**

- `1 <= nums1.length, nums2.length <= 1000`
- `0 <= nums1[i], nums2[i] <= 1000`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 使用set做 hash table.

<img src="./0349%20Intersection%20of%20Two%20Arrays.assets/20220707173513.png" alt="set哈希法" style="zoom:50%;" />

### 2. Important details

### 3. Complexity

- Time complexity:
- Space complexity:

<img src="./0349%20Intersection%20of%20Two%20Arrays.assets/image-20230703005326323.png" alt="image-20230703005326323" style="zoom:50%;" />

### 4. Code



```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        # 使用字典和集合
        hash_table = set(nums1)
        
        # 使用set存储结果, 自动去重
        result = set()
        for num in nums2:
            if num in hash_table:
                result.add(num)

        return list(result)
```



```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        # 使用字典和集合
        hash_table = {}
        for num in nums1:
            hash_table[num] = hash_table.get(num, 0) + 1
        
        # 使用set存储结果, 自动去重
        result = set()
        for num in nums2:
            if num in hash_table:
                result.add(num)

        return list(result)
```

- 使用数组做hash table

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        # array hash table
        hash_table = [0]*1001
        result = set()
        for num in nums1:
            hash_table[num] = 1
        for num in nums2:
            if hash_table[num] == 1:
                result.add(num)

        return result
```

- 使用python set

```python
class Solution:
    def intersection(self, nums1: List[int], nums2: List[int]) -> List[int]:
        return list(set(nums1) & set(nums2))
```

- Leetcode.com

```python
class Solution:
    def set_intersection(self, set1, set2):
        return [x for x in set1 if x in set2]
        
    def intersection(self, nums1, nums2):
        """
        :type nums1: List[int]
        :type nums2: List[int]
        :rtype: List[int]
        """  
        set1 = set(nums1)
        set2 = set(nums2)
        
        if len(set1) < len(set2):
            return self.set_intersection(set1, set2)
        else:
            return self.set_intersection(set2, set1)
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
