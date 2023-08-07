# [455. Assign Cookies](https://leetcode.com/problems/assign-cookies/)

## Problem

*****

Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child `i` has a greed factor `g[i]`, which is the minimum size of a cookie that the child will be content with; and each cookie `j` has a size `s[j]`. If `s[j] >= g[i]`, we can assign the cookie `j` to the child `i`, and the child `i` will be content. Your goal is to maximize the number of your content children and output the maximum number.

 

**Example 1:**

```
Input: g = [1,2,3], s = [1,1]
Output: 1
Explanation: You have 3 children and 2 cookies. The greed factors of 3 children are 1, 2, 3. 
And even though you have 2 cookies, since their size is both 1, you could only make the child whose greed factor is 1 content.
You need to output 1.
```

**Example 2:**

```
Input: g = [1,2], s = [1,2,3]
Output: 2
Explanation: You have 2 children and 3 cookies. The greed factors of 2 children are 1, 2. 
You have 3 cookies and their sizes are big enough to gratify all of the children, 
You need to output 2.
```

 

**Constraints:**

- `1 <= g.length <= 3 * 104`
- `0 <= s.length <= 3 * 104`
- `1 <= g[i], s[j] <= 231 - 1`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 贪心算法

### 1. Explanation

- 贪心算法

- 小饼干优先给小胃口小孩

### 2. Important details





### 3. Complexity

- Time complexity: O(mlogm + nlogn), 其中 m 和 n 分别是数组 g 和 的长度。对两个数组排序的时间复杂是O(mlogm + nlogn), 遍历数组的时间复杂度是O(m + n), 因此总时间复杂度是O(mlogm + n logn)
- Space complexity: O(logm + logn), 排序的额外空间开销。



### 4. Code

```python
class Solution:
    def findContentChildren(self, g: List[int], s: List[int]) -> int:
        # 贪心算法 - 小饼干优先给胃口小的孩子
        # sort
        g.sort()
        s.sort()
        childIndex = 0
        for cookieIndex in range(len(s)):
            if childIndex < len(g) and s[cookieIndex] >= g[childIndex]:
                childIndex += 1
        return childIndex
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
