# [135. Candy](https://leetcode.com/problems/candy/)

## Problem

*****

There are `n` children standing in a line. Each child is assigned a rating value given in the integer array `ratings`.

You are giving candies to these children subjected to the following requirements:

- Each child must have at least one candy.
- Children with a higher rating get more candies than their neighbors.

Return *the minimum number of candies you need to have to distribute the candies to the children*.

 

**Example 1:**

```
Input: ratings = [1,0,2]
Output: 5
Explanation: You can allocate to the first, second and third child with 2, 1, 2 candies respectively.
```

**Example 2:**

```
Input: ratings = [1,2,2]
Output: 4
Explanation: You can allocate to the first, second and third child with 1, 2, 1 candies respectively.
The third child gets 1 candy because it satisfies the above two conditions.
```

 

**Constraints:**

- `n == ratings.length`
- `1 <= n <= 2 * 104`
- `0 <= ratings[i] <= 2 * 104`

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 自解题的话要经常性的：
  - 画图
  - 模拟
  - 举例
  - 不要靠空想

- 类似于本题有两边比较的情况，不要两边一起比较，容易顾此失彼。应该先比较一边再比较另一边。这样逻辑比较清晰。

![135.分发糖果1](./0135%20Candy.assets/20201117115658791.png)

这在leetcode上是一道困难的题目，其难点就在于贪心的策略，如果在考虑局部的时候想两边兼顾，就会顾此失彼。

那么本题我采用了两次贪心的策略：

- 一次是从左到右遍历，只比较右边孩子评分比左边大的情况。
- 一次是从右到左遍历，只比较左边孩子评分比右边大的情况。

这样从局部最优推出了全局最优，即：相邻的孩子中，评分高的孩子获得更多的糖果



### 2. Important details





### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(N)`, candy list



### 4. Code

```python
class Solution:
    def candy(self, ratings: List[int]) -> int:
        candy = [1] * len(ratings)
        # 比较右边比左边大
        # 从前往后遍历, 从1开始遍历，因为比较i 和i -1
        for index in range(1, len(ratings)):
            # 只有大于，没有等于
            if ratings[index] > ratings[index - 1]:
                candy[index] = candy[index - 1] + 1
        # 比较左边比右边大
        # 从后往前遍历，从倒数第二个开始遍历，因为比较i和i + 1
        for index in range(len(ratings) - 2, -1, -1):
            if ratings[index] > ratings[index + 1]:
                candy[index] = max(candy[index + 1] + 1, candy[index])
        result = sum(candy)
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
