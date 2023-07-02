# 707. Design Linked List

## Problem

*****

Design your implementation of the linked list. You can choose to use a singly or doubly linked list.
A node in a singly linked list should have two attributes: `val` and `next`. `val` is the value of the current node, and `next` is a pointer/reference to the next node.
If you want to use the doubly linked list, you will need one more attribute `prev` to indicate the previous node in the linked list. Assume all nodes in the linked list are **0-indexed**.

Implement the `MyLinkedList` class:

- `MyLinkedList()` Initializes the `MyLinkedList` object.
- `int get(int index)` Get the value of the `indexth` node in the linked list. If the index is invalid, return `-1`.
- `void addAtHead(int val)` Add a node of value `val` before the first element of the linked list. After the insertion, the new node will be the first node of the linked list.
- `void addAtTail(int val)` Append a node of value `val` as the last element of the linked list.
- `void addAtIndex(int index, int val)` Add a node of value `val` before the `indexth` node in the linked list. If `index` equals the length of the linked list, the node will be appended to the end of the linked list. If `index` is greater than the length, the node **will not be inserted**.
- `void deleteAtIndex(int index)` Delete the `indexth` node in the linked list, if the index is valid.

 

**Example 1:**

```
Input
["MyLinkedList", "addAtHead", "addAtTail", "addAtIndex", "get", "deleteAtIndex", "get"]
[[], [1], [3], [1, 2], [1], [1], [1]]
Output
[null, null, null, null, 2, null, 3]

Explanation
MyLinkedList myLinkedList = new MyLinkedList();
myLinkedList.addAtHead(1);
myLinkedList.addAtTail(3);
myLinkedList.addAtIndex(1, 2);    // linked list becomes 1->2->3
myLinkedList.get(1);              // return 2
myLinkedList.deleteAtIndex(1);    // now the linked list is 1->3
myLinkedList.get(1);              // return 3
```

 

**Constraints:**

- `0 <= index, val <= 1000`
- Please do not use the built-in LinkedList library.
- At most `2000` calls will be made to `get`, `addAtHead`, `addAtTail`, `addAtIndex` and `deleteAtIndex`.

******

### 1. Classification

- 其实就是链表的增删查改

### 2. Discussion





*******

## Solution1

### 1. Explanation

<img src="./0707%20Design%20Linked%20List.assets/singly_get.png" alt="bla" style="zoom:50%;" />

<img src="./0707%20Design%20Linked%20List.assets/singly_insert.png" alt="bla" style="zoom:50%;" />

<img src="./0707%20Design%20Linked%20List.assets/singly_insert_head.png" alt="bla" style="zoom:50%;" />

<img src="./0707%20Design%20Linked%20List.assets/singly_delete.png" alt="bla" style="zoom:50%;" />

### 2. Important details

- 使用 `dummy_head`, 以简化头节点的处理。

- 注意检查`index`的合法性。

- 记得记录`size`的值。

- 在设置`current_node` 的时候，代入边界值看是否能获得正确的节点来确实需要设置为`dummy_head` 还是 `dummy_head.next`。

- `while` 里面 `index` 记得-1 ！！

- ==如果要处理第`index`个节点，那么需要找的是`index`前面那个节点，`index`节点一定是`current_node.next`==

  

### 3. Complexity

- Time complexity: `O(1)` for addAtHead. `O(k)` for get, addAtIndex, and deleteAtIndex, where `k` is an `index` of the element to get, add or delete. `O(N)` for addAtTail.

- Space complexity: `O(1)` for all operations.

  

### 4. Code

```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val = val
        self.next = next

class MyLinkedList:

    def __init__(self):
        """
        Set dummy_head and initial size.
        """
        self.dummy_head = ListNode()
        self.size = 0


    def get(self, index: int) -> int:
        """
        Get the value of the index node.
        """
        if index < 0 or index > self.size - 1:
            return -1
        current_node = self.dummy_head.next
        while index:
            current_node = current_node.next
            index -= 1
        return current_node.val


    def addAtHead(self, val: int) -> None:
        """
        Add a node of val before the head node.
        """
        new_node = ListNode(val)
        new_node.next = self.dummy_head.next
        self.dummy_head.next = new_node
        self.size += 1
        

    def addAtTail(self, val: int) -> None:
        """
        Append a node of value val as the last element of the
        linked list.
        """
        new_node = ListNode(val)
        current_node = self.dummy_head
        while current_node.next:
            current_node = current_node.next
        current_node.next = new_node
        self.size += 1


    def addAtIndex(self, index: int, val: int) -> None:
        """
        Add a node of value val before the indexth node in the linked list.
        """
        if index < 0 or index > self.size:
            return
        new_node = ListNode(val)
        current_node = self.dummy_head
        while index:
            current_node = current_node.next
            index -= 1
        new_node.next = current_node.next
        current_node.next = new_node
        self.size += 1
        

    def deleteAtIndex(self, index: int) -> None:
        """
        Delete the indexth node in the linked list.
        """
        if index < 0 or index > self.size - 1:
            return
        current_node = self.dummy_head
        while index:
            current_node = current_node.next
            index -= 1
        current_node.next = current_node.next.next
        self.size -= 1
    

# Your MyLinkedList object will be instantiated and called as such:
# obj = MyLinkedList()
# param_1 = obj.get(index)
# obj.addAtHead(val)
# obj.addAtTail(val)
# obj.addAtIndex(index,val)
# obj.deleteAtIndex(index)
```



********

## References

- [代码随想录 ](https://github.com/youngyangyang04/leetcode-master)
- [Leetcode.com](https://leetcode.com/problemset/all/)
