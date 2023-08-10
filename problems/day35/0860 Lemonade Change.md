# [860. Lemonade Change](https://leetcode.com/problems/lemonade-change/)

## Problem

*****

At a lemonade stand, each lemonade costs `$5`. Customers are standing in a queue to buy from you and order one at a time (in the order specified by bills). Each customer will only buy one lemonade and pay with either a `$5`, `$10`, or `$20` bill. You must provide the correct change to each customer so that the net transaction is that the customer pays `$5`.

Note that you do not have any change in hand at first.

Given an integer array `bills` where `bills[i]` is the bill the `ith` customer pays, return `true` *if you can provide every customer with the correct change, or* `false` *otherwise*.

 

**Example 1:**

```
Input: bills = [5,5,5,10,20]
Output: true
Explanation: 
From the first 3 customers, we collect three $5 bills in order.
From the fourth customer, we collect a $10 bill and give back a $5.
From the fifth customer, we give a $10 bill and a $5 bill.
Since all customers got correct change, we output true.
```

**Example 2:**

```
Input: bills = [5,5,10,10,20]
Output: false
Explanation: 
From the first two customers in order, we collect two $5 bills.
For the next two customers in order, we collect a $10 bill and give back a $5 bill.
For the last customer, we can not give the change of $15 back because we only have two $10 bills.
Since not every customer received the correct change, the answer is false.
```

 

**Constraints:**

- `1 <= bills.length <= 105`
- `bills[i]` is either `5`, `10`, or `20`.

******

### 1. Classification



### 2. Discussion





*******

## Solution1 greedy

### 1. Explanation

- 简单题，分情况讨论就好了

- 贪心的点在于：
  - 当遇到20的时候，先找10 + 5， 留下更多的5, 5更万能
  - 实在不行再找3个5

### 2. Important details





### 3. Complexity

- Time complexity:`O(N)` 
- Space complexity: `O(1)`



### 4. Code

```python
class Solution:
    def lemonadeChange(self, bills: List[int]) -> bool:
        changeFive, changeTen = 0, 0
        for index in range(len(bills)):
            if bills[index] == 5:
                changeFive += 1
            if bills[index] == 10:
                if changeFive >= 1:
                    changeFive -= 1
                    changeTen += 1
                else:
                    return False
            if bills[index] == 20:
                if changeTen >= 1 and changeFive >= 1:
                    # 优先找10 + 5
                    changeTen -= 1
                    changeFive -= 1
                elif changeFive >= 3:
                    # 不满足的话在找 5 * 3
                    changeFive -= 3
                else:
                    return False
        return True
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
