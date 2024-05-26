Given a `rows x cols` binary `matrix` filled with `0`'s and `1`'s, find the largest rectangle containing only `1`'s and return _its area_.
# Solution Complexity
- $O(mn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def maximalRectangle(self, matrix: List[List[str]]) -> int:
		# Sentinel value to perform calculations for heights left in monotonic stack
		heights, max_area = [0 for _ in range(len(matrix[0]) + 1)], 0

		for row in matrix:
			for idx, element in enumerate(row):
				heights[idx] = 0 if element == "0" else heights[idx] + 1

			# Sentinel value remove checking of size of stack, as there should not be any height below 0
			stack = [-1]
			for idx, height in enumerate(heights):
				# Maintain monotonic stack
				while height < heights[stack[-1]]:
					cur_height = heights[stack.pop()]
					# All heights between cur_height and height on top of stack will be higher or equal to cur_height
					max_area = max(max_area, (idx - stack[-1] - 1) * cur_height)
				stack.append(idx)

		return max_area
```