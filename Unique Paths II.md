You are given an `m x n` integer array `grid`. There is a robot initially located at the **top-left corner** (i.e., `grid[0][0]`). The robot tries to move to the **bottom-right corner** (i.e., `grid[m - 1][n - 1]`). The robot can only move either down or right at any point in time.

An obstacle and space are marked as `1` or `0` respectively in `grid`. A path that the robot takes cannot include **any** square that is an obstacle.

Return _the number of possible unique paths that the robot can take to reach the bottom-right corner_.

The testcases are generated so that the answer will be less than or equal to `2 * 109`.
# Solution Complexity
- $O(mn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def uniquePathsWithObstacles(self, obstacleGrid: List[List[int]]) -> int:
		dp = [[0 for _ in range(len(obstacleGrid[0]))] for _ in range(len(obstacleGrid))]

		for i in range(len(obstacleGrid)):
			for j in range(len(obstacleGrid[0])):
				if i == 0 and j == 0 and obstacleGrid[i][j] == 0:
					dp[i][j] = 1
					continue
				if obstacleGrid[i][j] == 0:
					from_top = 0 if i == 0 else dp[i - 1][j]
					from_left = 0 if j == 0 else dp[i][j - 1]
					dp[i][j] = from_top + from_left

		return dp[-1][-1]
```