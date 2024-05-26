We are given a list `schedule` of employees, which represents the working time for each employee.

Each employee has a list of non-overlapping `Intervals`, and these intervals are in sorted order.

Return the list of finite intervals representing **common, positive-length free time** for _all_ employees, also in sorted order.

(Even though we are representing `Intervals` in the form `[x, y]`, the objects inside are `Intervals`, not lists or arrays. For example, `schedule[0][0].start = 1`, `schedule[0][0].end = 2`, and `schedule[0][0][0]` is not defined).  Also, we wouldn't include intervals like [5, 5] in our answer, as they have zero length.
# Solution Complexity
- $O(nlogk)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
import heapq

"""
# Definition for an Interval.
class Interval:
    def __init__(self, start: int = None, end: int = None):
        self.start = start
        self.end = end
"""

class Solution:
	def employeeFreeTime(self, schedule: '[[Interval]]') -> '[Interval]':
		heap, free_times = [], []

		for employee in schedule:
			for i in employee:
				heapq.heappush(heap, (i.start, i.end))

		prev_end = None
		while len(heap) > 0:
			start, end = heapq.heappop(heap)
			print(start, end)
			if prev_end is None:
				prev_end = end
			elif start > prev_end:
				free_times.append(Interval(prev_end, start))
				print(prev_end, start)
			prev_end = max(prev_end, end)

		return free_times
```