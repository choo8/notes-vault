Given a `m x n` `grid` filled with non-negative numbers, find a path from top left to bottom right, which minimizes the sum of all numbers along its path.

**Note:** You can only move either down or right at any point in time.
# Solution Complexity
- $O(mn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def minPathSum(self, grid: List[List[int]]) -> int:
		dp = [[0 for _ in range(len(grid[0]))] for _ in range(len(grid))]
		dp[0][0] = grid[0][0]

		for i in range(len(grid)):
			for j in range(len(grid[0])):
				if i == 0 and j == 0:
					continue

				if i == 0:
					dp[i][j] = grid[i][j] + dp[i][j - 1]
				elif j == 0:
					dp[i][j] = grid[i][j] + dp[i - 1][j]
				else:
					dp[i][j] = grid[i][j] + min(dp[i][j - 1], dp[i - 1][j])

		return dp[-1][-1]
```