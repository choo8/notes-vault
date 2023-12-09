You are given an `m x n` `grid` where each cell can have one of three values:

- `0` representing an empty cell,
- `1` representing a fresh orange, or
- `2` representing a rotten orange.

Every minute, any fresh orange that is **4-directionally adjacent** to a rotten orange becomes rotten.

Return _the minimum number of minutes that must elapse until no cell has a fresh orange_. If _this is impossible, return_ `-1`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

class Solution:
	def orangesRotting(self, grid: List[List[int]]) -> int:
		queue = deque()
		num_minutes = 0

		for r in range(len(grid)):
			for c in range(len(grid[0])):
				if grid[r][c] == 2:
					queue.append((r, c))

		cur_round, has_fresh = [], False
		while len(queue) > 0:
			r, c = queue.popleft()

			for cur_r, cur_c in [(r + 1, c), (r - 1, c), (r, c - 1), (r, c + 1)]:
				if cur_r >= 0 and cur_r < len(grid) and cur_c >= 0 and cur_c < len(grid[0]) and grid[cur_r][cur_c] == 1:
					has_fresh = True
					grid[cur_r][cur_c] = 2
					cur_round.append((cur_r, cur_c))

			if len(queue) == 0:
				if has_fresh:
					num_minutes += 1

				for cur_r, cur_c in cur_round:
					queue.append((cur_r, cur_c))

				cur_round = []
				has_fresh = False

		for r in range(len(grid)):
			for c in range(len(grid[0])):
				if grid[r][c] == 1:
					return -1

		return num_minutes
```