Given an `m x n` `board` of characters and a list of strings `words`, return _all words on the board_.

Each word must be constructed from letters of sequentially adjacent cells, where **adjacent cells** are horizontally or vertically neighboring. The same letter cell may not be used more than once in a word.
# Solution Complexity
- $O(mnk + wk)$ time complexity
- $O(wk)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def findWords(self, board: List[List[str]], words: List[str]) -> List[str]:
		self.trie = {}
		self.res = []

		for word in words:
			self._addWord(word)

		for r in range(len(board)):
			for c in range(len(board[0])):
				if board[r][c] in self.trie:
					self._dfs(board, (r, c), set(), self.trie[board[r][c]])

		return self.res

	def _addWord(self, word: str) -> None:
		cur_node = self.trie

		for idx, c in enumerate(word):
			if c not in cur_node:
				cur_node[c] = {}

			if idx == len(word) - 1:
				cur_node[c]["#"] = word
			else:
				cur_node = cur_node[c]

	def _dfs(self, board: List[List[str]], coord: tuple[int, int], visited: set, trie: dict[str, dict]) -> None:
		if "#" in trie and not trie["#"] in self.res:
			self.res.append(trie["#"])

		if coord in visited:
			return

		visited.add(coord)
		r, c = coord

		for cur_r, cur_c in [(r - 1, c), (r + 1, c), (r, c - 1), (r, c + 1)]:
			if cur_r >= 0 and cur_r < len(board) and cur_c >= 0 and cur_c < len(board[0]) and (cur_r, cur_c) not in visited and board[cur_r][cur_c] in trie:
				self._dfs(board, (cur_r, cur_c), visited, trie[board[cur_r][cur_c]])

		visited.remove(coord)
		return
```