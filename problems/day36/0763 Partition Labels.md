# [763. Partition Labels](https://leetcode.com/problems/partition-labels/)

## Problem

*****

ou are given a string `s`. We want to partition the string into as many parts as possible so that each letter appears in at most one part.

Note that the partition is done so that after concatenating all the parts in order, the resultant string should be `s`.

Return *a list of integers representing the size of these parts*.

 

**Example 1:**

```
Input: s = "ababcbacadefegdehijhklij"
Output: [9,7,8]
Explanation:
The partition is "ababcbaca", "defegde", "hijhklij".
This is a partition so that each letter appears in at most one part.
A partition like "ababcbacadefegde", "hijhklij" is incorrect, because it splits s into less parts.
```

**Example 2:**

```
Input: s = "eccbbbbdec"
Output: [10]
```

 

**Constraints:**

- `1 <= s.length <= 500`
- `s` consists of lowercase English letters.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 greedy 模拟

### 1. Explanation

[题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0763.%E5%88%92%E5%88%86%E5%AD%97%E6%AF%8D%E5%8C%BA%E9%97%B4.md#%E6%80%9D%E8%B7%AF)

在遍历的过程中相当于是要找每一个字母的边界，**如果找到之前遍历过的所有字母的最远边界，说明这个边界就是分割点了**。此时前面出现过所有字母，最远也就到这个边界了。

可以分为如下两步：

- 统计每一个字符最后出现的位置
- 从头遍历字符，并更新字符的最远出现下标，如果找到字符最远出现位置下标和当前下标相等了，则找到了分割点

如图：

[![763.划分字母区间](./0763%20Partition%20Labels.assets/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303230313232323139313932343431372e706e67.png)](https://camo.githubusercontent.com/5a55501facb21dbc3c468df2c66fb432cd4f613d282d5c4c2feb67246c938b95/68747470733a2f2f636f64652d7468696e6b696e672d313235333835353039332e66696c652e6d7971636c6f75642e636f6d2f706963732f32303230313232323139313932343431372e706e67)



### 2. Important details

The `ord()` function in Python returns an integer representing the Unicode character. In simpler terms, it gives you the ASCII value (for 7-bit ASCII characters) or Unicode value (for other characters) of a given single character.

For example:

```python
print(ord('a'))  # Outputs: 97
print(ord('A'))  # Outputs: 65
print(ord('1'))  # Outputs: 49
print(ord(' '))  # Outputs: 32
```



### 3. Complexity

- Time complexity: O(n)
- Space complexity:  O(1)，使用的hash数组是固定大小 



### 4. Code

```python
class Solution:
    def partitionLabels(self, s: str) -> List[int]:
        # 使用一个hash数组来记录每个字母的最远出现坐标, 初始化为0
        hash = [0] * 27
        for index in range(len(s)):
            hash[ord(s[index]) - ord('a')] = index
        # 
        result = []
        # left and right to record left and right position.
        left, right = 0, 0
        for index in range(len(s)):
            right = max(right, hash[ord(s[index]) - ord('a')])
            if index == right:
                result.append(right - left + 1)
                left = right + 1
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
