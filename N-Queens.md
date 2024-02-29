The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return _all distinct solutions to the **n-queens puzzle**_. You may return the answer in **any order**.

Each solution contains a distinct board configuration of the n-queens' placement, where `'Q'` and `'.'` both indicate a queen and an empty space, respectively.
# Solution Complexity
- $O(n!)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def solveNQueens(self, n: int) -> List[List[str]]:
		self.solutions, self.col, self.diag1, self.diag2, self.queens = [], [0 for _ in range(n)], [0 for _ in range(2*n - 1)], [0 for _ in range(2*n - 1)], []
		self._search(0, n)
		return self.solutions

	def _search(self, row: int, n: int) -> None:
		if row == n:
			self.solutions.append(self._printBoard(self.queens, n))
			return 
		for pos in range(n):
			if self.col[pos] == 1 or self.diag1[row + pos] == 1 or self.diag2[pos - row + n - 1] == 1:
				continue
			self.col[pos], self.diag1[row + pos], self.diag2[pos - row + n - 1] = 1, 1, 1
			self.queens.append(pos)
			self._search(row + 1, n)
			self.col[pos], self.diag1[row + pos], self.diag2[pos - row + n - 1] = 0, 0, 0
			self.queens.pop()

	def _printBoard(self, queens: List[List[int]], n: int) -> List[List[str]]:
		board = [["." for _ in range(n)] for _ in range(n)]
		for row, col in enumerate(queens):
			board[row][col] = "Q"
		return ["".join(row) for row in board]
```