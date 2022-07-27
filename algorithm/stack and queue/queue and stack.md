# Queue

---

Created on: 7/25/2022

Modified on: 7/27/2022

---

Queue: FIFO (First-in First-out)

Design a simple queue:

``` python
class SimpleQueue():
    def __init__(self):
        self.__list = list()
    def enQueue(self, item):
        '''Add item to the queue'''
        self.__list.append(item)
    def deQueue(self):
        '''Delete item from the queue'''
        if self.__list:
            return self.__list.pop(0)
        else:
            return None
    def is_empty(self):
        '''Check if the queue is empty'''
        return self.__list
    def size(self):
        '''Return the length of queue'''
        return len(self.__list)
```

Design a circular queue:

``` python
class MyCircularQueue():
    def __init__(self, k: int):
        self.size = 0
        self.capacity = k
        self.head = 0
        self.queue = [0] * k

    def enQueue(self, value: int) -> bool:
        if self.size == self.capacity:
            return False
        tail = (self.head + self.size) % self.capacity
        self.queue[tail] = value
        self.size += 1
        return True

    def deQueue(self) -> bool:
        if self.size == 0:
            return False
        self.head = (self.head + 1) % self.capacity
        self.size -= 1
        return True

    def Front(self) -> int:
        if self.size == 0:
            return -1
        return self.queue[self.head]

    def Rear(self) -> int:
        if self.size == 0:
            return -1
        tail = (self.head + self.size - 1) % self.capacity
        return self.queue[tail]

    def isEmpty(self) -> bool:
        return self.size == 0

    def isFull(self) -> bool:
        return self.size == self.capacity
```

---

Design a minimum stack:

``` python
class MinStack():
    def __init__(self):
        self.stack = list()

    def push(self, val: int) -> None:
        self.stack.append(val)

    def pop(self) -> None:
        self.stack.pop()

    def top(self) -> int:
        return self.stack[-1]

    def getMin(self) -> int:
        return min(self.stack)
```