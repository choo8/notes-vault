Given an array of integers `heights` representing the histogram's bar height where the width of each bar is `1`, return _the area of the largest rectangle in the histogram_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asasdas
```Python
class Solution:
	def largestRectangleArea(self, heights: List[int]) -> int:
		stack = []
		res = 0

		for idx, h in enumerate(heights):
			if len(stack) == 0 or stack[-1][1] <= h:
				stack.append((idx, h))
			else:
				while len(stack) > 0 and stack[-1][1] > h:
					cur_idx, cur_h = stack.pop()
					if len(stack) > 0:
						res = max(res, (idx - stack[-1][0] - 1) * cur_h)
					else:
						res = max(res, idx * cur_h)
				stack.append((idx, h))

		while len(stack) > 0:
			cur_idx, cur_h = stack.pop()
			if len(stack) == 0:
				res = max(res, len(heights) * cur_h)
			else:
				res = max(res, (len(heights) - stack[-1][0] - 1) * cur_h)

		return res
```