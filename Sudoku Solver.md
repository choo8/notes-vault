Write a program to solve a Sudoku puzzle by filling the empty cells.

A sudoku solution must satisfy **all of the following rules**:

1. Each of the digits `1-9` must occur exactly once in each row.
2. Each of the digits `1-9` must occur exactly once in each column.
3. Each of the digits `1-9` must occur exactly once in each of the 9 `3x3` sub-boxes of the grid.

The `'.'` character indicates empty cells.
# Solution Complexity
- $O()$ time complexity
- $O()$ space complexity
# Thought Process
- 
# Solution
- sadadasd
```Python
class Solution:
	def solveSudoku(self, board: List[List[str]]) -> None:
		self.sorted_empty_cells = [idx for (idx, num_legal_moves) in self._sortedEmptyCells(board)]
		self._solve(board)

	def _solve(self, board: List[List[str]]) -> bool:
		if len(self.sorted_empty_cells) == 0:
			return True

		idx = self.sorted_empty_cells.pop()

		for val in range(1, 10):
			if self._isLegal(idx, val, board):
				board[x][y] = str(val)
				if self._solve(board):
					return True
		
		board[x][y] = "."
		self.sorted_empty_cells.append(idx)
		return False

	def _isLegal(self, idx: int, val: int, board: List[List[str]]) -> bool:
		x, y = idx // 9, idx % 9

		for i in range(9):
			if board[x][i] == str(val) or board[i][y] == str(val) or board[(int(x / 3) * 3) + (i // 3)][(int(y / 3) * 3) + (i % 3)] == str(val):
				return False

		return True

	def _sortedEmptyCells(self, board: List[List[str]]) -> List[int]:
		res = []

		for idx in range(81):
			x, y = idx // 9, idx % 9

			if board[x][y] == ".":
				num_legal_moves = 0
				
				for val in range(1, 10):
					if self._isLegal(idx, val, board):
						num_legal_moves += 1

				res.append((idx, num_legal_moves))

		return sorted(res, key=lambda x: x[1], reverse=True)
```