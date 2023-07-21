# Binary Tree Level Order Traversal

## Problem

*****



******

### 1. Classification



### 2. Discussion





*******

## Solution1



### 1. Explanation

- 层序遍历题目



### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        # Because need to delete the first left element, use deque here.
        queue = collections.deque([root])
        result = []
        while queue:
            # record the number of nodes in this level
            node_num = len(queue)
            level = []
            for _ in range(node_num):
                # save nodes in current level
                cur_node = queue.popleft()
                # remember: cur_node.val!
                level.append(cur_node.val)
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
            result.append(level)
        return result
```



### 107

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrderBottom(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        queue = collections.deque([root])
        result = []
        while queue:
            node_num = len(queue)
            level = []
            for _ in range(node_num):
                cur_node = queue.popleft()
                level.append(cur_node.val)
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
            result.append(level)
        # TC: O(N)
        result.reverse()
        return result
```



### 199

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
        # level order, but we only need the last one of each level.
        if not root:
            return []
        queue = collections.deque([root])
        result = []
        while queue:
            level_length = len(queue)
            for i in range(level_length):
                cur_node = queue.popleft()
                # Add left and right children to queue.
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
                # if cur_node is the last node of current level, add it to result.
                if i == level_length - 1:
                    result.append(cur_node.val)
        return result
        
```



### 637

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def averageOfLevels(self, root: Optional[TreeNode]) -> List[float]:
        if not root:
            return []
        queue = collections.deque([root])
        result = []
        while queue:
            level_length = len(queue)
            sum_of_level = 0
            for _ in range(level_length):
                cur_node = queue.popleft()
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
                sum_of_level += cur_node.val
            average_of_level = sum_of_level / level_length
            result.append(average_of_level)
        return result


```



### 429

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, children=None):
        self.val = val
        self.children = children
"""

class Solution:
    def levelOrder(self, root: 'Node') -> List[List[int]]:
        if not root:
            return []
        # Because need to delete the first left element, use deque here.
        queue = collections.deque([root])
        result = []
        while queue:
            # record the number of nodes in this level
            node_num = len(queue)
            level = []
            for _ in range(node_num):
                # save nodes in current level
                cur_node = queue.popleft()
                # remember: cur_node.val!
                level.append(cur_node.val)
                for children in cur_node.children:
                    queue.append(children)
            result.append(level)
        return result

```



### 515

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def largestValues(self, root: Optional[TreeNode]) -> List[int]:
        if not root:
            return []
        # Because need to delete the first left element, use deque here.
        queue = collections.deque([root])
        result = []
        while queue:
            # record the number of nodes in this level
            node_num = len(queue)
            max_of_level = float('-inf')
            for _ in range(node_num):
                # save nodes in current level
                cur_node = queue.popleft()
                # remember: cur_node.val!
                if cur_node.val >= max_of_level:
                    max_of_level = cur_node.val
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
            result.append(max_of_level)
        return result

```



### 169

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""

class Solution:
    def connect(self, root: 'Optional[Node]') -> 'Optional[Node]':
        if not root:
            return root
        # Because need to delete the first left element, use deque here.
        queue = collections.deque([root])
        result = []
        while queue:
            # record the number of nodes in this level
            node_num = len(queue)
            level = []
            for i in range(node_num):
                # save nodes in current level
                cur_node = queue.popleft()
                if i != node_num - 1:
                    cur_node.next = queue[0]
                else:
                    cur_node.next = None
                # remember: cur_node.val!
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
        return root

```



### 117

与116 相同

```python
"""
# Definition for a Node.
class Node:
    def __init__(self, val: int = 0, left: 'Node' = None, right: 'Node' = None, next: 'Node' = None):
        self.val = val
        self.left = left
        self.right = right
        self.next = next
"""

class Solution:
    def connect(self, root: 'Node') -> 'Node':
        if not root:
            return root
        # Because need to delete the first left element, use deque here.
        queue = collections.deque([root])
        result = []
        while queue:
            # record the number of nodes in this level
            node_num = len(queue)
            level = []
            for i in range(node_num):
                # save nodes in current level
                cur_node = queue.popleft()
                if i != node_num - 1:
                    cur_node.next = queue[0]
                else:
                    cur_node.next = None
                # remember: cur_node.val!
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
        return root
```



### 104

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def maxDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        # Because need to delete the first left element, use deque here.
        queue = collections.deque([root])
        level = 0
        while queue:
            # record the number of nodes in this level
            node_num = len(queue)
            for _ in range(node_num):
                cur_node = queue.popleft()
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
            level += 1
        return level
```

### 111

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def minDepth(self, root: Optional[TreeNode]) -> int:
        if not root:
            return 0
        # Because need to delete the first left element, use deque here.
        queue = collections.deque([root])
        depth = 0
        while queue:
            # record the number of nodes in this level
            node_num = len(queue)
            level = []
            for _ in range(node_num):
                # save nodes in current level
                cur_node = queue.popleft()
                if not cur_node.left and not cur_node.right:
                    return depth + 1
                if cur_node.left:
                    queue.append(cur_node.left)
                if cur_node.right:
                    queue.append(cur_node.right)
            depth += 1
        return depth

```



********



## Solution2

### 1. Explanation

- `range(len(queue))`

在 Python 中，`range(len(queue))` 创建的是一个固定的序列，这个序列的长度在创建时就确定了，不会随着后续的队列长度变化而变化。这是因为 `range()` 函数在调用时就已经计算了参数的值，之后的循环不会再重新计算参数。

在这段代码中，`len(queue)` 会在每次外部循环开始时计算一次。这是因为我们每次循环都会重新调用 `range(len(queue))`。每次调用 `range(len(queue))` 时，`len(queue)` 都会立即计算，并且在整个内部循环过程中，该值保持不变。这就是为什么我们说 `len(queue)` 只在每次外部循环开始时被计算一次。

例如，如果队列中有三个元素，那么 `range(len(queue))` 就会创建一个序列 `[0, 1, 2]`。然后在内部的 `for` 循环中，即使队列中增加了新的元素，这个序列也不会改变，仍然是 `[0, 1, 2]`，循环也就只会执行三次。这确保了我们只处理了开始时队列中的三个元素，而不包括后来添加到队列中的元素。

- 在python中用deque和用list模拟队列的区别是什么?

Python的`list`和`collections.deque`都可以被用来模拟队列（queue）数据结构，但是在性能上有一些关键的区别。

Python的`list`内置数据结构在插入和删除元素时的性能表现和元素在列表中的位置有关。对于在列表的末尾插入和删除元素，`list`的性能是非常高的，时间复杂度为O(1)。但是，如果你在列表的开头插入或删除元素，那么`list`需要移动其他所有元素来填补或释放空间，这会导致时间复杂度为O(n)。

相比之下，`collections.deque`是一个双端队列（double-ended queue）结构，支持在两端插入和删除元素的操作，且这些操作的时间复杂度都是O(1)。所以，当你需要频繁地在队列的头部插入或删除元素时，使用`collections.deque`会有更高的性能。

在你的代码中，你使用了`deque`的`append`方法将元素添加到队列的末尾，和`popleft`方法从队列的头部移除元素，这些操作都是O(1)复杂度。如果你用`list`替换`deque`，那么`popleft`操作就会变成O(n)复杂度，可能会显著降低你代码的性能。

### 2. Important details





### 3. Complexity

- Time complexity:
- Space complexity:



### 4. Code

```python
# 利用长度法
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
        if not root:
            return []
        queue = collections.deque([root])
        result = []
        while queue:
            level = []
            for _ in range(len(queue)):
                cur = queue.popleft()
                level.append(cur.val)
                if cur.left:
                    queue.append(cur.left)
                if cur.right:
                    queue.append(cur.right)
            result.append(level)
        return result
```

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](