Given an `n x n` binary matrix `grid`, return _the length of the shortest **clear path** in the matrix_. If there is no clear path, return `-1`.

A **clear path** in a binary matrix is a path from the **top-left** cell (i.e., `(0, 0)`) to the **bottom-right** cell (i.e., `(n - 1, n - 1)`) such that:

- All the visited cells of the path are `0`.
- All the adjacent cells of the path are **8-directionally** connected (i.e., they are different and they share an edge or a corner).

The **length of a clear path** is the number of visited cells of this path.
# Solution Complexity
- $O(n^2)$ time complexity
- $O(n^2)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

class Solution:
	def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
		if len(grid) == 0 or len(grid[0]) == 0 or grid[0][0] == 1:
			return -1

		queue, visited = deque([(0, 0, 1)]), set()

		directions = [(-1, -1), (0, -1), (1, -1), (1, 0), (1, 1), (0, 1), (-1, 1), (-1, 0)]
		while len(queue) > 0:
			cur_x, cur_y, cur_path = queue.popleft()

			if cur_x == len(grid) - 1 and cur_y == len(grid[0]) - 1:
				return cur_path

			for dx, dy in directions:
				new_x, new_y = cur_x + dx, cur_y + dy
				if self._isLegal(new_x, new_y, grid) and grid[new_x][new_y] == 0 and (new_x, new_y) not in visited:
					visited.add((new_x, new_y))
					queue.append((new_x, new_y, cur_path + 1))

		return -1

	def _isLegal(self, x: int, y: int, grid: List[List[int]]) -> bool:
		return x >= 0 and x < len(grid) and y >= 0 and y < len(grid[0])
```