You are given an array of non-overlapping intervals `intervals` where `intervals[i] = [starti, endi]` represent the start and the end of the `ith` interval and `intervals` is sorted in ascending order by `starti`. You are also given an interval `newInterval = [start, end]` that represents the start and end of another interval.

Insert `newInterval` into `intervals` such that `intervals` is still sorted in ascending order by `starti` and `intervals` still does not have any overlapping intervals (merge overlapping intervals if necessary).

Return `intervals` _after the insertion_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def insert(self, intervals: List[List[int]], newInterval: List[int]) -> List[List[int]]:
		for idx, i in enumerate(intervals):
			if self._intersect(i, newInterval):
				intervals[idx][0], intervals[idx][1] = min(i[0], newInterval[0]), max(i[1], newInterval[1])

				while idx + 1 < len(intervals) and self._intersect(intervals[idx], intervals[idx + 1]):
					intervals[idx][0], intervals[idx][1] = min(i[0], intervals[idx + 1][0]), max(i[1], intervals[idx + 1][1])
					intervals.pop(idx + 1)
				break

			if newInterval[1] < i[0]:
				intervals.insert(idx, newInterval)
				break

			if i[1] < newInterval[0] and (idx + 1 == len(intervals) or newInterval[1] < intervals[idx + 1][0]):
				intervals.insert(idx + 1, newInterval)
				break

		if len(intervals) == 0:
			return [newInterval]
		else:
			return intervals

	def _intersect(self, i1: List[int], i2: List[int]) -> bool:
		if i2[0] < i1[0]:
			i1, i2 = i2, i1

		return i2[0] <= i1[1]
```