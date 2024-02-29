Given an `m x n` integers `matrix`, return _the length of the longest increasing path in_ `matrix`.

From each cell, you can either move in four directions: left, right, up, or down. You **may not** move **diagonally** or move **outside the boundary** (i.e., wrap-around is not allowed).
# Solution Complexity
- $O(mn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdad
```Python
from itertools import product

class Solution:
	def longestIncreasingPath(self, matrix: List[List[int]]) -> int:
		stack, dp, ret = [], [[1 for _ in range(len(matrix[0]))] for _ in range(len(matrix))], 1

		graph = {(m, n): {"parents": 0, "children": set()} for m, n in product(range(len(matrix)), range(len(matrix[0])))}

		for m in range(len(matrix)):
			for n in range(len(matrix[0])):
				for cur_m, cur_n in [(m - 1, n), (m, n - 1), (m + 1, n), (m, n + 1)]:
					if cur_m >= 0 and cur_n >= 0 and cur_m < len(matrix) and cur_n < len(matrix[0]) and matrix[cur_m][cur_n] < matrix[m][n]:
						graph[(m, n)]["parents"] += 1
						graph[(cur_m, cur_n)]["children"].add((m, n))

				if graph[(m, n)]["parents"] == 0:
					stack.append((m, n))

		visited = set()
		while len(stack) > 0:
			cur_m, cur_n = stack.pop()

			visited.add((cur_m, cur_n))

			for child_m, child_n in graph[(cur_m, cur_n)]["children"]:
				dp[child_m][child_n] = max(dp[child_m][child_n], dp[cur_m][cur_n] + 1)
				ret = max(ret, dp[child_m][child_n])

				graph[(child_m, child_n)]["parents"] -= 1

				if graph[(child_m, child_n)]["parents"] == 0:
					stack.append((child_m, child_n))

		return ret
```