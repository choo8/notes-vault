You are given an `m x n` integer matrix `matrix` with the following two properties:

- Each row is sorted in non-decreasing order.
- The first integer of each row is greater than the last integer of the previous row.

Given an integer `target`, return `true` _if_ `target` _is in_ `matrix` _or_ `false` _otherwise_.

You must write a solution in `O(log(m * n))` time complexity.
# Solution Complexity
- $O(log (m * n))$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def searchMatrix(self, matrix: List[List[int]], target: int) -> bool:
		row_idx = self._findRow(0, len(matrix), matrix, target)

		return self._search(0, len(matrix[0]) - 1, matrix[row_idx], target)

	def _search(self, left: int, right: int, row: List[int], target:int) -> bool:
		if left > right:
			return False

		mid = left + (right - left) // 2

		if row[mid] == target:
			return True
		elif row[mid] < target:
			return self._search(mid + 1, right, row, target)
		else:
			return self._search(left, mid - 1, row, target)

	def _findRow(self, top: int, bottom: int, matrix: List[List[int]], target: int) -> int:
		if top + 1 >= bottom:
			if bottom < len(matrix) and target >= matrix[bottom][0]:
				return bottom
			else:
				return top

		mid = top + (bottom - top) // 2

		if matrix[mid][0] < target:
			return self._findRow(mid, bottom, matrix, target)
		elif target < matrix[mid][0]:
			return self._findRow(top, mid - 1, matrix, target)
		else:
			return mid
```