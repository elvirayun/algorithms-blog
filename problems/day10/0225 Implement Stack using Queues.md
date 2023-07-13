# 225. Implement Stack using Queues

## Problem

*****

Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (`push`, `top`, `pop`, and `empty`).

Implement the `MyStack` class:

- `void push(int x)` Pushes element x to the top of the stack.
- `int pop()` Removes the element on the top of the stack and returns it.
- `int top()` Returns the element on the top of the stack.
- `boolean empty()` Returns `true` if the stack is empty, `false` otherwise.

**Notes:**

- You must use **only** standard operations of a queue, which means that only `push to back`, `peek/pop from front`, `size` and `is empty` operations are valid.
- Depending on your language, the queue may not be supported natively. You may simulate a queue using a list or deque (double-ended queue) as long as you use only a queue's standard operations.

 

**Example 1:**

```
Input
["MyStack", "push", "push", "top", "pop", "empty"]
[[], [1], [2], [], [], []]
Output
[null, null, null, 2, 2, false]

Explanation
MyStack myStack = new MyStack();
myStack.push(1);
myStack.push(2);
myStack.top(); // return 2
myStack.pop(); // return 2
myStack.empty(); // return False
```

 

**Constraints:**

- `1 <= x <= 9`
- At most `100` calls will be made to `push`, `pop`, `top`, and `empty`.
- All the calls to `pop` and `top` are valid.

 

**Follow-up:** Can you implement the stack using only one queue?

******

### 1. Classification



### 2. Discussion





*******

## Solution1 Using one queue

### 1. Explanation

**一个队列在模拟栈弹出元素的时候只要将队列头部的元素（除了最后一个元素外） 重新添加到队列尾部，此时再去弹出元素就是栈的顺序了。**

### 2. Important details

### 3. Complexity

- Time complexity: pop -> `O(N)`,  others -> `O(1)`
- Space complexity: `O(N)`



### 4. Code

```python
from collections import deque

#  Implement stack using one queue.
class MyStack:

    def __init__(self):
        self.queue = deque()
        
        
    def push(self, x: int) -> None:
        self.queue.append(x)


    def pop(self) -> int:
        # Move all elments to the back of the queue, except the last one.
        for i in range(len(self.queue) - 1):
            self.queue.append(self.queue.popleft())
        # Pop the last elment.
        return self.queue.popleft()

    def top(self) -> int:
        return self.queue[-1]


    def empty(self) -> bool:
        return not self.queue


# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()
```



********

## Solution2 Using two queues

### 1. Explanation

![225.用队列实现栈](./0225%20Implement%20Stack%20using%20Queues.assets/225.%E7%94%A8%E9%98%9F%E5%88%97%E5%AE%9E%E7%8E%B0%E6%A0%88.gif)



### 2. Important details

- We can not use `self.queue = self.queue_back` to copy deque, because it's a shallow copy, which means if we change the elements in one of the deques, then both deques elements will be changed.

- 在python 中list 等数据结构存的是里面元素的地址，所以如果是shallow copy, 则两个list的元素地址们是相同的，所以在其中一个list修改，另一个也会被修改。

### 3. Complexity

- Time complexity: pop -> `O(N)`,  others -> `O(1)`
- Space complexity:  `O(N)`



### 4. Code

```python
from collections import deque

#  Implement stack using two queues.
class MyStack:

    def __init__(self):
        # 一个queue用于出栈, 一个queue用于保存
        self.queue = deque()
        self.queue_save = deque()
        
        
    def push(self, x: int) -> None:
        self.queue.append(x)


    def pop(self) -> int:
        for i in range(len(self.queue) - 1):
            self.queue_save.append(self.queue.popleft())
        res = self.queue.popleft()
        # self.queue = self.queue_save
        # put them back to `self.queue` from `self.queue_save`
        for i in range(len(self.queue_save)):
            self.queue.append(self.queue_save.popleft())
        return res


    def top(self) -> int:
        return self.queue[-1]


    def empty(self) -> bool:
        return not self.queue


# Your MyStack object will be instantiated and called as such:
# obj = MyStack()
# obj.push(x)
# param_2 = obj.pop()
# param_3 = obj.top()
# param_4 = obj.empty()
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
