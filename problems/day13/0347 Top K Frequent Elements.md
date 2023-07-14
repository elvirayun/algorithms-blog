# 347. Top K Frequent Elements

## Problem

*****

Given an integer array `nums` and an integer `k`, return *the* `k` *most frequent elements*. You may return the answer in **any order**.

 

**Example 1:**

```
Input: nums = [1,1,1,2,2,3], k = 2
Output: [1,2]
```

**Example 2:**

```
Input: nums = [1], k = 1
Output: [1]
```

 

**Constraints:**

- `1 <= nums.length <= 105`
- `-104 <= nums[i] <= 104`
- `k` is in the range `[1, the number of unique elements in the array]`.
- It is **guaranteed** that the answer is **unique**.

 

**Follow up:** Your algorithm's time complexity must be better than `O(n log n)`, where n is the array's size.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 使用小顶堆

### 1. Explanation

![347.前K个高频元素](./0347%20Top%20K%20Frequent%20Elements.assets/68747470733a2f2f636f64652d7468696e6b696e672e63646e2e626365626f732e636f6d2f706963732f3334372e2545352538392538444b2545342542382541412545392541422539382545392541322539312545352538352538332545372542342541302e6a7067.jpeg)



### 2. Important details

- ` heapq.heappush(minHeap, (freq, num))`
  - 堆（Heap）在 Python 中是通过完全二叉树来实现的，这意味着堆中元素的排序会基于元素的值，而元组的排序则是基于元组中第一个元素的值。如果第一个元素的值相同，才会比较第二个元素的值。
  - 所以这里把freq放在前面



### 3. Complexity

- Time complexity: `O(NlogK)`,  N 是nums的长度，K是需要的前K个数
- Space complexity: `O(N)` 



### 4. Code

```python
import heapq

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        map = {}
        # 构建值和频率的map
        for num in nums:
            map[num] = map.get(num, 0) + 1
        
        # 维护只有k个的小顶堆
        minHeap = []
        for num, freq in map.items():
            heapq.heappush(minHeap, (freq, num))
            if len(minHeap) > k:
                heapq.heappop(minHeap)
        
        # 返回值
        result = [0] * k
        for i in range(k - 1, -1, -1):
            result[i] = heapq.heappop(minHeap)[1]
        return result
```



********

## Solution2 调用python库函数简化代码

### 1. Explanation

这个解决方案已经非常有效了，但是有一些小的优化可以考虑：

1. 当构建频率字典时，可以直接使用 Python 的 collections.Counter，它可以自动统计每个元素出现的次数，减少代码量。
2. Python 的 heapq 模块提供了一个 nlargest 方法，可以直接返回堆中的前 K 大元素，这样就不需要自己手动维护一个大小为 K 的堆了。

### 2. Important details



### 3. Complexity

- Time complexity: `O(NlogK)`
- Space complexity: `O(N)`



### 4. Code

```python
from collections import Counter
import heapq

class Solution:
    def topKFrequent(self, nums: List[int], k: int) -> List[int]:
        map = Counter(nums)

        return [item[0] for item in heapq.nlargest(k, map.items(),key=lambda x:x[1])]
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
