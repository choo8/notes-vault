Given an `m x n` binary `matrix` filled with `0`'s and `1`'s, _find the largest square containing only_ `1`'s _and return its area_.
# Solution Complexity
- $O(mn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
import sys

class Solution:
	def maximalSquare(self, matrix: List[List[str]]) -> int:
		dp, ret = [[0 for _ in range(len(matrix[0]))] for _ in range(len(matrix))], 0

		for i in range(len(matrix)):
			for j in range(len(matrix[0])):
				if matrix[i][j] == "1":
					cur_len = sys.maxsize

					if i > 0 and j > 0:
						cur_len = min(cur_len, dp[i - 1][j - 1], dp[i - 1][j], dp[i][j - 1])

					if cur_len == sys.maxsize:
						cur_len = 0

					dp[i][j] = cur_len + 1
					ret = max(ret, dp[i][j] ** 2)

		return ret
```