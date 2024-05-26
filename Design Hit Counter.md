Design a hit counter which counts the number of hits received in the past `5` minutes (i.e., the past `300` seconds).

Your system should accept a `timestamp` parameter (**in seconds** granularity), and you may assume that calls are being made to the system in chronological order (i.e., `timestamp` is monotonically increasing). Several hits may arrive roughly at the same time.

Implement the `HitCounter` class:

- `HitCounter()` Initializes the object of the hit counter system.
- `void hit(int timestamp)` Records a hit that happened at `timestamp` (**in seconds**). Several hits may happen at the same `timestamp`.
- `int getHits(int timestamp)` Returns the number of hits in the past 5 minutes from `timestamp` (i.e., the past `300` seconds).
# Solution Complexity
- $O(1)$ time complexity for `hit` operation and $O(n)$ time complexity for `getHits` operation
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

class HitCounter:
	def __init__(self):
		self.queue = deque()

	def hit(self, timestamp: int) -> None:
		self.queue.append(timestamp)

	def getHits(self, timestamp: int) -> int:
		while len(self.queue) > 0 and timestamp - self.queue[0] >= 300:
			self.queue.popleft()
		return len(self.queue)


# Your HitCounter object will be instantiated and called as such:
# obj = HitCounter()
# obj.hit(timestamp)
# param_2 = obj.getHits(timestamp)
```