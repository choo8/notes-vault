Given an `m x n` matrix `mat`, return _an array of all the elements of the array in a diagonal order_.
# Solution Complexity
- $O(mn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def findDiagonalOrder(self, mat: List[List[int]]) -> List[int]:
		elements = []

		state, x, y = True, 0, 0
		while len(elements) < len(mat) * len(mat[0]):
			elements.append(mat[y][x])
			state, x, y = self._nextElement(state, mat, x, y)

		return elements

	def _nextElement(self, state: bool, mat: List[List[int]], x: int, y: int) -> List[int]:
		if state:
			if x == len(mat[0]) - 1:
				return [not state, x, y + 1]
			elif y == 0:
				return [not state, x + 1, y]
			else:
				return [state, x + 1, y - 1]
		else:
			if y == len(mat) - 1:
				return [not state, x + 1, y]
			elif x == 0:
				return [not state, x, y + 1]
			else:
				return [state, x - 1, y + 1]
```