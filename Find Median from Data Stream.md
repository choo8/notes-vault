The **median** is the middle value in an ordered integer list. If the size of the list is even, there is no middle value, and the median is the mean of the two middle values.

- For example, for `arr = [2,3,4]`, the median is `3`.
- For example, for `arr = [2,3]`, the median is `(2 + 3) / 2 = 2.5`.

Implement the MedianFinder class:

- `MedianFinder()` initializes the `MedianFinder` object.
- `void addNum(int num)` adds the integer `num` from the data stream to the data structure.
- `double findMedian()` returns the median of all elements so far. Answers within `10-5` of the actual answer will be accepted.
# Solution Complexity
- $O(logn)$ time complexity for `addNum` and $O(1)$ time complexity for `findMedian`
- $O(n)$ space complexity
# Thought Process
# Solution
- adasd
```Python
import heapq

class MedianFinder:
	def __init__(self):
		self.left_heap = []
		self.right_heap = []

	def addNum(self, num: int) -> None:
		if len(self.right_heap) == 0:
			heapq.heappush(self.right_heap, num)
		elif len(self.left_heap) == len(self.right_heap):
			if num > -self.left_heap[0]:
				heapq.heappush(self.right_heap, num)
			else:
				cur = heapq.heappop(self.left_heap)
				heapq.heappush(self.left_heap, -num)
				heapq.heappush(self.right_heap, -cur)
		else:
			if num < self.right_heap[0]:
				heapq.heappush(self.left_heap, -num)
			else:
				cur = heapq.heappop(self.right_heap)
				heapq.heappush(self.left_heap, -cur)
				heapq.heappush(self.right_heap, num)

	def findMedian(self) -> float:
		if len(self.right_heap) > len(self.left_heap):
			return self.right_heap[0]
		else:
			return (float(-self.left_heap[0]) + float(self.right_heap[0])) / 2.0

# Your MedianFinder object will be instantiated and called as such:
# obj = MedianFinder()
# obj.addNum(num)
# param_2 = obj.findMedian()
```