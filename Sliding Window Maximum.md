You are given an array of integers `nums`, there is a sliding window of size `k` which is moving from the very left of the array to the very right. You can only see the `k` numbers in the window. Each time the sliding window moves right by one position.

Return _the max sliding window_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
- 
# Solution
- sdfsdf
```Python
from collections import deque

class Monoqueue:
	def __init__(self):
		self.queue = deque()

	def push(self, n: int) -> None:
		while len(self.queue) != 0 and self.queue[0] < n:
			self.queue.popleft()
		self.queue.appendleft(n)

	def pop(self, n: int) -> None:
		if self.queue[-1] == n:
			self.queue.pop()

	def peek(self) -> int:
		return self.queue[-1]

class Solution:
	def maxSlidingWindow(self, nums: List[int], k: int) -> List[int]:
		monoqueue = Monoqueue()
		res = []

		for i in range(k):
			monoqueue.push(nums[i])

		res.append(monoqueue.peek())

		for i in range(k, len(nums)):
				monoqueue.pop(nums[i - k])
				monoqueue.push(nums[i])
				res.append(monoqueue.peek())

		return res
```