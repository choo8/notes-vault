Given an array of meeting time intervals `intervals` where `intervals[i] = [start_i, end_i]`, return the minimum number of conference rooms required.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
import heapq

class Solution:
	def minMeetingRooms(self, intervals: List[List[int]]) -> int:
		heap = []

		for i in sorted(intervals):
			if len(heap) > 0 and heap[0] <= i[0]:
				heapq.heappop(heap)
			heapq.heappush(heap, i[1])

		return len(heap)
```