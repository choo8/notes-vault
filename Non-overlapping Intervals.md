Given an array of intervals `intervals` where `intervals[i] = [starti, endi]`, return _the minimum number of intervals you need to remove to make the rest of the intervals non-overlapping_.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def eraseOverlapIntervals(self, intervals: List[List[int]]) -> int:
		cur_idx, ret = 0, 0
		intervals.sort()

		while cur_idx < len(intervals) - 1:
			if self._overlap(intervals[cur_idx], intervals[cur_idx + 1]):
				ret += 1
				if intervals[cur_idx][1] < intervals[cur_idx + 1][1]:
					intervals[cur_idx + 1] = intervals[cur_idx]
				
			cur_idx += 1

		return ret

	def _overlap(self, i1: List[int], i2: List[int]) -> bool:
		if i1[0] > i2[0]:
			i1, i2 = i2, i1

		return i1[1] > i2[0]
```