# [332. Reconstruct Itinerary](https://leetcode.com/problems/reconstruct-itinerary/)

#backtracking



## Problem

*****

You are given a list of airline `tickets` where `tickets[i] = [fromi, toi]` represent the departure and the arrival airports of one flight. Reconstruct the itinerary in order and return it.

All of the tickets belong to a man who departs from `"JFK"`, thus, the itinerary must begin with `"JFK"`. If there are multiple valid itineraries, you should return the itinerary that has the smallest lexical order when read as a single string.

- For example, the itinerary `["JFK", "LGA"]` has a smaller lexical order than `["JFK", "LGB"]`.

You may assume all tickets form at least one valid itinerary. You must use all the tickets once and only once.

 

**Example 1:**

![img](./0332%20Reconstruct%20Itinerary.assets/itinerary1-graph.jpg)

```
Input: tickets = [["MUC","LHR"],["JFK","MUC"],["SFO","SJC"],["LHR","SFO"]]
Output: ["JFK","MUC","LHR","SFO","SJC"]
```

**Example 2:**

![img](./0332%20Reconstruct%20Itinerary.assets/itinerary2-graph.jpg)

```
Input: tickets = [["JFK","SFO"],["JFK","ATL"],["SFO","ATL"],["ATL","JFK"],["ATL","SFO"]]
Output: ["JFK","ATL","JFK","SFO","ATL","SFO"]
Explanation: Another possible reconstruction is ["JFK","SFO","ATL","JFK","ATL","SFO"] but it is larger in lexical order.
```

 

**Constraints:**

- `1 <= tickets.length <= 300`
- `tickets[i].length == 2`
- `fromi.length == 3`
- `toi.length == 3`
- `fromi` and `toi` consist of uppercase English letters.
- `fromi != toi`

******

### 1. Classification



### 2. Discussion





*******

## Solution1 回溯算法

### 1. Explanation

- [题解](https://github.com/youngyangyang04/leetcode-master/blob/master/problems/0332.%E9%87%8D%E6%96%B0%E5%AE%89%E6%8E%92%E8%A1%8C%E7%A8%8B.md)



### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
from collections import defaultdict

class Solution:
    def backtracking(self, targets, path, ticketNum) -> bool:
        if len(path) == ticketNum + 1:
            # 找到有效行程
            return True
        # 当前机场
        curAirport = path[-1] 
        # 当前机场可以到达的目的地列表
        destinations = targets[curAirport]
        for i, dest in enumerate(destinations):
            # 标记已经使用的机票（删除）
            targets[curAirport].pop(i)
            # 添加目的地路径
            path.append(dest)
            if self.backtracking(targets, path, ticketNum):
                # 找到一个有效行程即可
                return True
            # 回溯
            targets[curAirport].insert(i, dest)
            path.pop()
        # 没有找到有效行程
        return False

    def findItinerary(self, tickets: List[List[str]]) -> List[str]:
        targets = defaultdict(list)
        for ticket in tickets:
            targets[ticket[0]].append(ticket[1])
        # 对目的地列表进行排序
        for airpor in targets:
            targets[airpor].sort()
        # 
        path = ["JFK"]
        self.backtracking(targets, path, len(tickets))
        return path
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
