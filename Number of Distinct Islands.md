You are given an `m x n` binary matrix `grid`. An island is a group of `1`'s (representing land) connected **4-directionally** (horizontal or vertical.) You may assume all four edges of the grid are surrounded by water.

An island is considered to be the same as another if and only if one island can be translated (and not rotated or reflected) to equal the other.

Return _the number of **distinct** islands_.
# Solution Complexity
- $O(mn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def numDistinctIslands(self, grid: List[List[int]]) -> int:
		num_islands = 0
		visited, shapes = set(), set()
		directions = [(-1, 0), (1, 0), (0, -1), (0, 1)]

		for i in range(len(grid)):
			for j in range(len(grid[0])):
				if (i, j) in visited or grid[i][j] == 0:
					continue

				stack = [(i, j)]
				shape = []

				while len(stack) > 0:
					x, y = stack.pop()
					visited.add((x, y))
					shape.append((x - i, y - j))

					for dx, dy in directions:
						cur_x, cur_y = x + dx, y + dy
						if self._isLegal(grid, cur_x, cur_y) and grid[cur_x][cur_y] == 1 and (cur_x, cur_y) not in visited:
							stack.append((cur_x, cur_y))

				shape = tuple(shape)
				if shape not in shapes:
					shapes.add(shape)
					num_islands += 1

		return num_islands

	def _isLegal(self, grid: List[List[int]], x: int, y: int) -> bool:
		return x >= 0 and x < len(grid) and y >= 0 and y < len(grid[0])
```