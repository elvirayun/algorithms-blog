# [406. Queue Reconstruction by Height](https://leetcode.com/problems/queue-reconstruction-by-height/)

## Problem

*****

You are given an array of people, `people`, which are the attributes of some people in a queue (not necessarily in order). Each `people[i] = [hi, ki]` represents the `ith` person of height `hi` with **exactly** `ki` other people in front who have a height greater than or equal to `hi`.

Reconstruct and return *the queue that is represented by the input array* `people`. The returned queue should be formatted as an array `queue`, where `queue[j] = [hj, kj]` is the attributes of the `jth` person in the queue (`queue[0]` is the person at the front of the queue).

 

**Example 1:**

```
Input: people = [[7,0],[4,4],[7,1],[5,0],[6,1],[5,2]]
Output: [[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]]
Explanation:
Person 0 has height 5 with no other people taller or the same height in front.
Person 1 has height 7 with no other people taller or the same height in front.
Person 2 has height 5 with two persons taller or the same height in front, which is person 0 and 1.
Person 3 has height 6 with one person taller or the same height in front, which is person 1.
Person 4 has height 4 with four people taller or the same height in front, which are people 0, 1, 2, and 3.
Person 5 has height 7 with one person taller or the same height in front, which is person 1.
Hence [[5,0],[7,0],[5,2],[6,1],[4,4],[7,1]] is the reconstructed queue.
```

**Example 2:**

```
Input: people = [[6,0],[5,0],[4,0],[3,2],[2,2],[1,4]]
Output: [[4,0],[5,0],[2,2],[3,2],[1,4],[6,0]]
```

 

**Constraints:**

- `1 <= people.length <= 2000`
- `0 <= hi <= 106`
- `0 <= ki < people.length`
- It is guaranteed that the queue can be reconstructed.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

![406.根据身高重建队列](./0406%20Queue%20Reconstruction%20by%20Height.assets/20201216201851982.png)

**局部最优：优先按身高高的people的k来插入。插入操作过后的people满足队列属性**

**全局最优：最后都做完插入操作，整个队列满足题目队列属性**

局部最优可推出全局最优，找不出反例，那就试试贪心。

关于出现两个维度一起考虑的情况，我们已经做过两道题目了，另一道就是[135. 分发糖果 (opens new window)](https://programmercarl.com/0135.分发糖果.html)。

**其技巧都是确定一边然后贪心另一边，两边一起考虑，就会顾此失彼**。



- Python list 插入元素时间复杂度

  在Python中，`list` 是基于数组的数据结构。插入元素的时间复杂度取决于插入的位置。

  1. **在末尾插入** (`append` 方法)：这通常是一个 O(1) 的操作，但在某些情况下，当底层数组需要扩容时，它可能会达到 O(n)。但是，由于扩容操作是分摊的，所以 `append` 的平均时间复杂度仍然是 O(1)。

  2. **在开始或中间插入** (`insert` 方法)：这是一个 O(n) 的操作，因为你可能需要移动插入点之后的所有元素来为新元素腾出空间。

  例如，如果你有一个包含 5 个元素的列表 `[a, b, c, d, e]` 并且你在索引 1（即元素 `b` 之前）插入一个新元素 `x`，你需要移动 `b, c, d, e` 这四个元素来为 `x` 腾出空间。所以，插入操作的时间复杂度是 O(n)，其中 n 是需要移动的元素数量。

  总之，插入元素的时间复杂度取决于插入的位置。在列表的末尾插入通常是最快的，而在开始或中间插入可能需要更多的时间。



### 2. Important details





### 3. Complexity

- Time complexity: `O(nlogn + n^2)`,  排序`O(logn)`, 后面再for循环中插入，python list 插入时间复杂度`O(n^2)`

  Space complexity: `O(n)`, que的空间



### 4. Code

```python
class Solution:
    def reconstructQueue(self, people: List[List[int]]) -> List[List[int]]:
        # 先根据高度h进行排序
        people.sort(key=lambda x: (-x[0], x[1]))
        que = []
        # 再根据k值插入
        for p in people:
            index = p[1]
            que.insert(index, p)
        return que
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
