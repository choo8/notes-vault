You are given an `n x n` binary matrix `grid`. You are allowed to change **at most one** `0` to be `1`.

Return _the size of the largest **island** in_ `grid` _after applying this operation_.

An **island** is a 4-directionally connected group of `1`s.
# Solution Complexity
- $O(n^2)$ time complexity
- $O(n^2)$ space complexity
# Thought Process
# Solution
- asdad
```Python
from collections import deque

class Solution:
	def largestIsland(self, grid: List[List[int]]) -> int:
		largest, size, parent, visited, directions = 0, {}, {}, set(), [(0, 1), (0, -1), (-1, 0), (1, 0)]
		for i in range(len(grid)):
			for j in range(len(grid[0])):
				if grid[i][j] == 1 and (i, j) not in visited:
					queue = deque([(i, j)])
					parent[(i, j)] = (i, j)
					size[(i, j)] = 0

					while len(queue) > 0:
						cur_i, cur_j = queue.popleft()

						if (cur_i, cur_j) in visited:
							continue
						visited.add((cur_i, cur_j))

						parent[(cur_i, cur_j)] = (i, j)
						size[(i, j)] += 1

						for di, dj in directions:
							new_i, new_j = cur_i + di, cur_j + dj
							if self._isLegal(new_i, new_j, grid) and grid[new_i][new_j] == 1 and (new_i, new_j) not in visited:
								queue.append((new_i, new_j))

					largest = max(largest, size[(i, j)])

		for i in range(len(grid)):
			for j in range(len(grid[0])):
				if grid[i][j] == 0:
					cur_size, visited = 1, set()

					for di, dj in directions:
						new_i, new_j = i + di, j + dj

						if self._isLegal(new_i, new_j, grid) and (new_i, new_j) in parent and parent[(new_i, new_j)] not in visited:
							cur_size += size[parent[(new_i, new_j)]]
							visited.add(parent[(new_i, new_j)])

					largest = max(largest, cur_size)

		return largest

	def _isLegal(self, i: int, j: int, grid: List[List[int]]) -> bool:
		return i >= 0 and i < len(grid) and j >= 0 and j < len(grid[0])
```