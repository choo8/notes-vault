Given an `m x n` integer matrix `matrix`, if an element is `0`, set its entire row and column to `0`'s.

You must do it [in place](https://en.wikipedia.org/wiki/In-place_algorithm).
# Solution Complexity
- $O(mn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def setZeroes(self, matrix: List[List[int]]) -> None:
		first_row, first_col = False, False

		for c in range(len(matrix[0])):
			if matrix[0][c] == 0:
				first_row = True
				break

		for r in range(len(matrix)):
			if matrix[r][0] == 0:
				first_col = True
				break

		for r in range(1, len(matrix)):
			for c in range(1, len(matrix[0])):
				if matrix[r][c] == 0:
					matrix[r][0] = 0
					matrix[0][c] = 0

		for c in range(1, len(matrix[0])):
			if matrix[0][c] == 0:
				for r in range(1, len(matrix)):
					matrix[r][c] = 0

		for r in range(1, len(matrix)):
			if matrix[r][0] == 0:
				for c in range(1, len(matrix[0])):
					matrix[r][c] = 0

		if first_row:
			for c in range(len(matrix[0])):
				matrix[0][c] = 0

		if first_col:
			for r in range(len(matrix)):
				matrix[r][0] = 0
```