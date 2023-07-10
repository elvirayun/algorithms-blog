# 541. Reverse String II

## Problem

*****

Given a string `s` and an integer `k`, reverse the first `k` characters for every `2k` characters counting from the start of the string.

If there are fewer than `k` characters left, reverse all of them. If there are less than `2k` but greater than or equal to `k` characters, then reverse the first `k` characters and leave the other as original.

 

**Example 1:**

```
Input: s = "abcdefg", k = 2
Output: "bacdfeg"
```

**Example 2:**

```
Input: s = "abcd", k = 2
Output: "bacd"
```

 

**Constraints:**

- `1 <= s.length <= 104`
- `s` consists of only lowercase English letters.
- `1 <= k <= 104`

******

### 1. Classification



### 2. Discussion



*******

## Solution1

### 1. Explanation

- [How to Reverse a String in Python - W3Schools](https://www.w3schools.com/python/python_howto_reverse_string.asp)

- 比自己写的简洁很多，思路是相似的，但是要学会化简思维和代码	

### 2. Important details

- 注意一般库函数区间都是左闭右开
- Python 对 `str` 进行切片或者`reverse` 等操作是在新地址上重新创建一个`str`, 所以这里的`reverseSubSt`是需要 `return S` 的

### 3. Complexity

- Time complexity: `O(N)`
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def reverseSubStr(self, s:str, left:int, right:int) -> str:
        # 地址会不一样，所以要返回s
        s = s[:left] + s[left:right][::-1] + s[right:]
        return s


    def reverseStr(self, s: str, k: int) -> str:
        # Two pointers - left, right
        for left in range(0, len(s), 2 * k):
            right = left + k
            s = self.reverseSubStr(s, left, right)
        return s
```



********

## Solution2 自己写出来的解法 也是双指针

### 1. Explanation





### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
class Solution:
    def reverseStr(self, s: str, k: int) -> str:
        s_list = list(s)
        s_length = len(s_list)
        # 还是双指针法
        # 每次left和right先在同一个位置
        left, right = 0, 0
        remaining_length = s_length


        while remaining_length > 0:
            # 如果剩余的长度>=k, 那么right就相对于left多k-1
            if remaining_length >= k:
                right += k - 1
            # 如果剩余长度 <k, 那么right直接到最后一个位置
            else:
                right = s_length - 1

            # 开始交换, 用tmp来交换
            left_tmp, right_tmp = left, right
            for step in range((right - left + 1) // 2):
                s_list[left_tmp], s_list[right_tmp]  = s_list[right_tmp], s_list[left_tmp]
                left_tmp += 1
                right_tmp -= 1

            # 每次减掉2k长度  
            remaining_length -= 2 * k
            left += 2 * k
            right = left

        return ''.join(s_list)
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
