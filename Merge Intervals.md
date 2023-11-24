Given an array of `intervals` where `intervals[i] = [starti, endi]`, merge all overlapping intervals, and return _an array of the non-overlapping intervals that cover all the intervals in the input_.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def merge(self, intervals: List[List[int]]) -> List[List[int]]:
		res = []

		for i in sorted(intervals):
			if len(res) != 0 and i[0] <= res[-1][1]:
				res[-1][1] = max(res[-1][1], i[1])
			else:
				res.append(i)

		return res
```