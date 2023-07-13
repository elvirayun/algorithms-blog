# 232. Implement Queue using Stacks

## Problem

*****

mplement a first in first out (FIFO) queue using only two stacks. The implemented queue should support all the functions of a normal queue (`push`, `peek`, `pop`, and `empty`).

Implement the `MyQueue` class:

- `void push(int x)` Pushes element x to the back of the queue.
- `int pop()` Removes the element from the front of the queue and returns it.
- `int peek()` Returns the element at the front of the queue.
- `boolean empty()` Returns `true` if the queue is empty, `false` otherwise.

**Notes:**

- You must use **only** standard operations of a stack, which means only `push to top`, `peek/pop from top`, `size`, and `is empty` operations are valid.
- Depending on your language, the stack may not be supported natively. You may simulate a stack using a list or deque (double-ended queue) as long as you use only a stack's standard operations.

 

**Example 1:**

```
Input
["MyQueue", "push", "push", "peek", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 1, 1, false]

Explanation
MyQueue myQueue = new MyQueue();
myQueue.push(1); // queue is: [1]
myQueue.push(2); // queue is: [1, 2] (leftmost is front of the queue)
myQueue.peek(); // return 1
myQueue.pop(); // return 1, queue is [2]
myQueue.empty(); // return false
```

 

**Constraints:**

- `1 <= x <= 9`
- At most `100` calls will be made to `push`, `pop`, `peek`, and `empty`.
- All the calls to `pop` and `peek` are valid.

 

**Follow-up:** Can you implement the queue such that each operation is **[amortized](https://en.wikipedia.org/wiki/Amortized_analysis)** `O(1)`time complexity? In other words, performing `n` operations will take overall `O(n)` time even if one of those operations may take longer.

******

### 1. Classification



### 2. Discussion





*******

## Solution1

### 1. Explanation

- 两个栈： 一个主要负责push, 一个主要负责pop

- 每次需要pop的时候如果stack_out为空，则把stack_in的数据全部输入进stack_out再进行pop。

  如果stack_out里面有数据，则直接pop出来stack_out的数据



### 2. Important details





### 3. Complexity

- Time complexity: push() and empty() `O(1)`; pop() and peek() `O(N)`
- Space complexity: `O(N)`



### 4. Code

```python
class MyQueue:

    def __init__(self):
        """
        stack_in主要负责push, satck_out主要负责pop
        """
        self.stack_in = []
        self.stack_out = []
        

    def push(self, x: int) -> None:
        self.stack_in.append(x)
        

    def pop(self) -> int:
        if not self.stack_out:
            while(self.stack_in):
                self.stack_out.append(self.stack_in.pop())
        return self.stack_out.pop()


    def peek(self) -> int:
        res = self.pop()
        self.stack_out.append(res)
        return res

    def empty(self) -> bool:
        return not self.stack_in and not self.stack_out


# Your MyQueue object will be instantiated and called as such:
# obj = MyQueue()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.peek()
# param_4 = obj.empty()
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
