Given an `m x n` grid of characters `board` and a string `word`, return `true` _if_ `word` _exists in the grid_.

The word can be constructed from letters of sequentially adjacent cells, where adjacent cells are horizontally or vertically neighboring. The same letter cell may not be used more than once.
# Solution Complexity
- $O(m^2n^2)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdsd
```Python
class Solution:
	def exist(self, board: List[List[str]], word: str) -> bool:
		self.exists = False

		for m in range(len(board)):
			for n in range(len(board[0])):
				if board[m][n] == word[0]:
					visited = set([(m, n)])
					self._dfs(board, word, (m, n), 0, visited)
					if self.exists:
						return True

		return False

	def _dfs(self, board: List[List[str]], word: str, board_idx: tuple[int, int], word_idx: int, visited: set[int]) -> None:
		if word_idx == len(word) - 1:
			self.exists = True
			return

		for dm, dn in [(-1, 0), (1, 0), (0, -1), (0, 1)]:
			m, n = board_idx[0] + dm, board_idx[1] + dn

			if (m, n) not in visited and m >= 0 and m < len(board) and n >= 0 and n < len(board[0]) and board[m][n] == word[word_idx + 1]:
				visited.add((m, n))
				self._dfs(board, word, (m, n), word_idx + 1, visited)
				visited.remove((m, n))
```