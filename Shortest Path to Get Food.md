You are starving and you want to eat food as quickly as possible. You want to find the shortest path to arrive at any food cell.

You are given an `m x n` character matrix, `grid`, of these different types of cells:

- `'*'` is your location. There is **exactly one** `'*'` cell.
- `'#'` is a food cell. There may be **multiple** food cells.
- `'O'` is free space, and you can travel through these cells.
- `'X'` is an obstacle, and you cannot travel through these cells.

You can travel to any adjacent cell north, east, south, or west of your current location if there is not an obstacle.

Return _the **length** of the shortest path for you to reach **any** food cell_. If there is no path for you to reach food, return `-1`.
# Solution Complexity
- $O(mn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdad
```Python
from collections import deque

class Solution:
	def getFood(self, grid: List[List[str]]) -> int:
		# Obtain location of self
		self_location = None
		for i in range(len(grid)):
			for j in range(len(grid[0])):
				if grid[i][j] == "*":
					self_location = (i, j, 0) # Last element to track path length
					break

		# BFS to find nearest food cell
		queue, visited, directions = deque([self_location]), set(), [(0, 1), (0, -1), (-1, 0), (1, 0)]
		while len(queue) > 0:
			i, j, cur_length = queue.popleft()

			if (i, j) in visited:
				continue
			else:
				visited.add((i, j))

			for di, dj in directions:
				cur_i, cur_j = i + di, j + dj
				if self.isLegal(grid, cur_i, cur_j):
					if grid[cur_i][cur_j] == "#":
						return cur_length + 1
					elif grid[cur_i][cur_j] == "O":
						queue.append((cur_i, cur_j, cur_length + 1))

		return -1

	def isLegal(self, grid: List[List[str]], i: int, j: int) -> bool:
		return i >= 0 and i < len(grid) and j >= 0 and j < len(grid[0])
```