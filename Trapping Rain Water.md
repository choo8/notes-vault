Given `n` non-negative integers representing an elevation map where the width of each bar is `1`, compute how much water it can trap after raining.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def trap(self, height: List[int]) -> int:
		res = 0
		stack = []

		for idx, h in enumerate(height):
			if h > 0 and (len(stack) == 0 or stack[-1][1] > h):
				if len(stack) > 0:
					res += min(stack[-1][1], h) * (idx - stack[-1][0] - 1)
				stack.append((idx, h))
			elif h > 0:
				prev_h = 0
				while len(stack) > 0 and stack[-1][1] <= h:
					cur_idx, cur_h = stack.pop()
					res += (min(cur_h, h) - prev_h) * (idx - cur_idx - 1)
					prev_h = cur_h
				if len(stack) > 0:
					res += (h - prev_h) * (idx - stack[-1][0] - 1)
				stack.append((idx, h))

		return res
```