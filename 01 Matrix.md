Given an `m x n` binary matrix `mat`, return _the distance of the nearest_ `0` _for each cell_.

The distance between two adjacent cells is `1`.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- sdfsaf
```Python
class Solution:
	def updateMatrix(self, mat: List[List[int]]) -> List[List[int]]:
		for r in range(len(mat)):
			for c in range(len(mat[0])):
				if mat[r][c] != 0:
					top = mat[r - 1][c] if r - 1 >= 0 else len(mat) * len(mat[0])
					left = mat[r][c - 1] if c - 1 >= 0 else len(mat) * len(mat[0])
					mat[r][c] = min(top, left) + 1

		for r in range(len(mat) - 1, -1, -1):
			for c in range(len(mat[0]) - 1, -1, -1):
				if mat[r][c] != 0:
					bottom = mat[r + 1][c] if r + 1 < len(mat) else len(mat) * len(mat[0])
					right = mat[r][c + 1] if c + 1 < len(mat[0]) else len(mat) * len(mat[0])
					mat[r][c] = min(mat[r][c], min(bottom, right) + 1)

		return mat
```