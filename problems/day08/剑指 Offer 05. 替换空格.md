# 剑指 Offer 05. 替换空格

## Problem

*****

请实现一个函数，把字符串 `s` 中的每个空格替换成"%20"。

**示例 1：**

```
输入：s = "We are happy."
输出："We%20are%20happy."
```

**限制：**

```
0 <= s 的长度 <= 10000
```

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 关键：双指针，从后往前移。

- **其实很多数组填充类的问题，都可以先预先给数组扩容带填充后的大小，然后在从后向前进行操作。**
- Python中因为字符串是不可变类型，所以操作字符串需要将其转换为列表，因此空间复杂度不可能为`O(1)` 。


### 2. Important details



### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)` , 忽略在python中str要转成数组的空间复杂度话是`O(1)`。



### 4. Code

```python
class Solution:
    def replaceSpace(self, s: str) -> str:
        counter = s.count(' ')
        s_list = list(s)
        # 每遇到一个空格就扩展两个格子
        s_list.extend(' '* counter * 2)
        # i,j分别指向s的最后位置，和扩展后的s的最后位置
        i, j = len(s) - 1, len(s_list) - 1
        
        while i >= 0:
            if s_list[i] != ' ':
                s_list[j] = s_list[i]
                j -= 1
                i -= 1
            else:
                # 左闭右开
                s_list[ j - 2 :j + 1] = '%20'
                j = j - 3
                i -= 1
        return ''.join(s_list)
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
