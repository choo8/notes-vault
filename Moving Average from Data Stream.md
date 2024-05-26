Given a stream of integers and a window size, calculate the moving average of all integers in the sliding window.

Implement the `MovingAverage` class:

- `MovingAverage(int size)` Initializes the object with the size of the window `size`.
- `double next(int val)` Returns the moving average of the last `size` values of the stream.
# Solution Complexity
- $O(1)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

class MovingAverage:
	def __init__(self, size: int):
		self.size = size
		self.queue = deque()
		self.integer_sum = 0

	def next(self, val: int) -> float:
		if len(self.queue) == self.size:
			self.integer_sum -= self.queue.popleft()
		self.queue.append(val)
		self.integer_sum += val
		return float(self.integer_sum) / len(self.queue)


# Your MovingAverage object will be instantiated and called as such:
# obj = MovingAverage(size)
# param_1 = obj.next(val)
```