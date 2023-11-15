Design your implementation of the circular queue. The circular queue is a linear data structure in which the operations are performed based on FIFO (First In First Out) principle, and the last position is connected back to the first position to make a circle. It is also called "Ring Buffer".

One of the benefits of the circular queue is that we can make use of the spaces in front of the queue. In a normal queue, once the queue becomes full, we cannot insert the next element even if there is a space in front of the queue. But using the circular queue, we can use the space to store new values.

Implement the `MyCircularQueue` class:

- `MyCircularQueue(k)` Initializes the object with the size of the queue to be `k`.
- `int Front()` Gets the front item from the queue. If the queue is empty, return `-1`.
- `int Rear()` Gets the last item from the queue. If the queue is empty, return `-1`.
- `boolean enQueue(int value)` Inserts an element into the circular queue. Return `true` if the operation is successful.
- `boolean deQueue()` Deletes an element from the circular queue. Return `true` if the operation is successful.
- `boolean isEmpty()` Checks whether the circular queue is empty or not.
- `boolean isFull()` Checks whether the circular queue is full or not.

You must solve the problem without using the built-in queue data structure in your programming language.
# Solution Complexity
- $O(1)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class MyCircularQueue:
	def __init__(self, k: int):
		self.q = [0] * k
		self.start, self.end, self.num_val = -1, -1, 0

	def Front(self) -> int:
		if self.start != -1:
			return self.q[self.start]
		else:
			return -1

	def Rear(self) -> int:
		if self.end != -1:
			return self.q[self.end]
		else:
			return -1

	def enQueue(self, value: int) -> bool:
		if self.start == -1 and self.end == -1:
			self.start, self.end, self.num_val = 0, 0, 1
			self.q[self.start] = value
			return True
		elif self.num_val == len(self.q):
			return False
		else:
			self.num_val += 1
			self.end = (self.end + 1) % len(self.q)
			self.q[self.end] = value
			return True

	def deQueue(self) -> bool:
		if self.start == -1 and self.end == -1:
			return False
		elif self.num_val == 1:
			self.start, self.end, self.num_val = -1, -1, 0
			return True
		else:
			self.num_val -= 1
			self.start = (self.start + 1) % len(self.q)
			return True

	def isEmpty(self) -> bool:
		return self.num_val == 0

	def isFull(self) -> bool:
		return self.num_val == len(self.q)
```