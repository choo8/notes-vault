Given an array of meeting time `intervals` where `intervals[i] = [starti, endi]`, determine if a person could attend all meetings.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def canAttendMeetings(self, intervals: List[List[int]]) -> bool:
		cur = 0

		for i in sorted(intervals):
			if cur > i[0]:
				return False
			cur = i[1]

		return True
```