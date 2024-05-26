The **n-queens** puzzle is the problem of placing `n` queens on an `n x n` chessboard such that no two queens attack each other.

Given an integer `n`, return _the number of distinct solutions to the **n-queens puzzle**_.
# Solution Complexity
- $O(n!)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def totalNQueens(self, n: int) -> int:
		self.n, self.num_sol = n, 0
		self.cols, self.diags1, self.diags2 = [False for _ in range(n)], [False for _ in range((2 * n) - 1)], [False for _ in range((2 * n) - 1)]
		self._solve(0)
		return self.num_sol

	def _solve(self, n: int) -> None:
		if n == self.n:
			self.num_sol += 1
			return

		for i in range(self.n):
			if not self.cols[i] and not self.diags1[i + n] and not self.diags2[self.n - 1 - i + n]:
				self.cols[i], self.diags1[i + n], self.diags2[self.n - 1 - i + n] = True, True, True
				self._solve(n + 1)
				self.cols[i], self.diags1[i + n], self.diags2[self.n - 1 - i + n] = False, False, False

		return
```