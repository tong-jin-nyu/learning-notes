# Queue

---

Created on: 7/25/2022

Modified on: 7/25/2022

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
class CircularQueue():
    def __init__(self, capacity: int):
        self.size = 0
        self.capacity = capacity
        self.head = 0
```
