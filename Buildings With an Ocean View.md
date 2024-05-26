There are `n` buildings in a line. You are given an integer array `heights` of size `n` that represents the heights of the buildings in the line.

The ocean is to the right of the buildings. A building has an ocean view if the building can see the ocean without obstructions. Formally, a building has an ocean view if all the buildings to its right have a **smaller** height.

Return a list of indices **(0-indexed)** of buildings that have an ocean view, sorted in increasing order.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def findBuildings(self, heights: List[int]) -> List[int]:
		stack = []
		for idx in range(len(heights) - 1, -1, -1):
			if len(stack) == 0 or heights[idx] > stack[-1][1]:
				stack.append((idx, heights[idx]))

		building_indices = []
		while len(stack) > 0:
			idx, _ = stack.pop()
			building_indices.append(idx)

		return building_indices
```