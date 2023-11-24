Given an array of integers `temperatures` represents the daily temperatures, return _an array_ `answer` _such that_ `answer[i]` _is the number of days you have to wait after the_ `ith` _day to get a warmer temperature_. If there is no future day for which this is possible, keep `answer[i] == 0` instead.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adasda
```Python
class Solution:
	def dailyTemperatures(self, temperatures: List[int]) -> List[int]:
		answer = [0] * len(temperatures)
		stack = []

		for idx, t in enumerate(temperatures):
			while len(stack) != 0 and stack[-1][0] < t:
				cur_temp, cur_idx = stack.pop()
				answer[cur_idx] = idx - cur_idx
			stack.append((t, idx))

		return answer
```