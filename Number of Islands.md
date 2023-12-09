Given an `m x n` 2D binary grid `grid` which represents a map of `'1'`s (land) and `'0'`s (water), return _the number of islands_.

An **island** is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

class Solution:
	def numIslands(self, grid: List[List[str]]) -> int:
		queue = deque()
		visited = set()
		num_islands = 0

		for r in range(len(grid)):
			for c in range(len(grid[0])):
				if grid[r][c] == "0" or (r, c) in visited:
					continue

				num_islands += 1
				queue.append((r, c))
				visited.add((r, c))

				while len(queue) > 0:
					cur_r, cur_c = queue.popleft()

					for _cur_r, _cur_c in [(cur_r - 1, cur_c), (cur_r + 1, cur_c), (cur_r, cur_c - 1), (cur_r, cur_c + 1)]:
						if _cur_r >= 0 and _cur_c >= 0 and _cur_r < len(grid) and _cur_c < len(grid[0]) and grid[_cur_r][_cur_c] == "1" and (_cur_r, _cur_c) not in visited:
							queue.append((_cur_r, _cur_c))
							visited.add((_cur_r, _cur_c))

		return num_islands
```