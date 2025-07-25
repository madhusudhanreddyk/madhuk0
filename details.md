### Data structure tutorial exercise: Queue

For all exercises use Queue class implemented in main tutorial.

1. Design a food ordering system where your python program will run two threads,

    i. Place Order: This thread will be placing an order and inserting that into a queue. This thread places new order every 0.5 second. (hint: use time.sleep(0.5) function)

    ii. Serve Order: This thread will server the order. All you need to do is to pop the order out of the queue and print it. This thread serves an order every 2 seconds. Also start this thread 1 second after place order thread is started.

Use this video to get yourself familiar with multithreading in python.

Pass following list as an argument to place order thread,

```python
orders = ['pizza','samosa','pasta','biryani','burger']
```

This problem is a producer,consumer problem where place_order thread is producing orders whereas server_order thread is consuming the food orders. Use Queue class implemented in a video tutorial.

<details>
<summary>Solution</summary>

```python
import threading
import time

from collections import deque

class Queue:
    def __init__(self):
        self.buffer = deque()

    def enqueue(self, val):
        self.buffer.appendleft(val)

    def dequeue(self):
        if len(self.buffer)==0:
            print("Queue is empty")
            return
        return self.buffer.pop()

    def is_empty(self):
        return len(self.buffer) == 0

    def size(self):
        return len(self.buffer)
# ... (rest of your code)
```
</details>
