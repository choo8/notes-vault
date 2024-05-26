In an **infinite** chess board with coordinates from `-infinity` to `+infinity`, you have a **knight** at square `[0, 0]`.

A knight has 8 possible moves it can make, as illustrated below. Each move is two squares in a cardinal direction, then one square in an orthogonal direction.
# Solution Complexity
- $O(1)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from collections import deque

class Solution:
	def minKnightMoves(self, x: int, y: int) -> int:
		directions = [(1, 2), (2, 1), (2, -1), (1, -2), (-1, -2), (-2, -1), (-2, 1), (-1, 2)]
		queue, visited = deque([(0, 0, 0)]), set()

		while len(queue) > 0:
			cur_x, cur_y, num_moves = queue.popleft()

			if (cur_x, cur_y) == (x, y):
				return num_moves

			if (cur_x, cur_y) in visited:
				continue
			visited.add((cur_x, cur_y))

			for dx, dy in directions:
				queue.append((cur_x + dx, cur_y + dy, num_moves + 1))
```