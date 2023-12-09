There is an m x n rectangular island that borders both the Pacific Ocean and Atlantic Ocean. The Pacific Ocean touches the island's left and top edges, and the Atlantic Ocean touches the island's right and bottom edges.

The island is partitioned into a grid of square cells. You are given an `m x n` integer matrix `heights` where `heights[r][c]` represents the height above sea level of the cell at coordinate `(r, c)`.

The island receives a lot of rain, and the rain water can flow to neighboring cells directly north, south, east, and west if the neighboring cell's height is less than or equal to the current cell's height. Water can flow from any cell adjacent to an ocean into the ocean.

Return a 2D list of grid coordinates `result` where `result[i] = [r_i, c_i]` denotes that rain water can flow from cell `(r_i, c_i)` to both the Pacific and Atlantic oceans.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque
from typing import Set

class Solution:
	def pacificAtlantic(self, heights: List[List[int]]) -> List[List[int]]:
		pacific_q, atlantic_q = deque(), deque()
		
		for r in range(len(heights)):
			pacific_q.append((r, 0))
			atlantic_q.append((r, len(heights[0]) - 1))

		for c in range(len(heights[0])):
			pacific_q.append((0, c))
			atlantic_q.append((len(heights) - 1, c))

		pacific_visited, atlantic_visited = self._bfs(heights, pacific_q), self._bfs(heights, atlantic_q)

		return [[r, c] for (r, c) in pacific_visited.intersection(atlantic_visited)]

	def _bfs(self, heights: List[List[int]], ocean_q: deque) -> Set:
		visited = set(ocean_q)

		while len(ocean_q) > 0:
			r, c = ocean_q.popleft()

			for cur_r, cur_c in [(r - 1, c), (r + 1, c), (r, c - 1), (r, c + 1)]:
				if cur_r >= 0 and cur_r < len(heights) and cur_c >= 0 and cur_c < len(heights[0]) and heights[cur_r][cur_c] >= heights[r][c] and (cur_r, cur_c) not in visited:
					ocean_q.append((cur_r, cur_c))
					visited.add((cur_r, cur_c))

		return visited
```