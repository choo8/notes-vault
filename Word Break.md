Given a string `s` and a dictionary of strings `wordDict`, return `true` if `s` can be segmented into a space-separated sequence of one or more dictionary words.

**Note** that the same word in the dictionary may be reused multiple times in the segmentation.
# Solution Complexity
- $O(n^2)$ time complexity
- $O(mk)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def wordBreak(self, s: str, wordDict: List[str]) -> bool:
		trie = {}
		dp = [False] * len(s)

		for word in wordDict:
			self._addWord(word, trie)

		for idx in range(len(s)):
			dp[idx] = self._searchWord(s[:idx + 1], trie)

			for j in range(idx):
				if dp[idx]:
					break

				if dp[j]:
					dp[idx] = self._searchWord(s[j + 1:idx + 1], trie)

		return dp[-1]

	def _addWord(self, word: str, trie: dict[str, dict]) -> None:
		cur_node = trie

		for idx, c in enumerate(word):
			if c not in cur_node:
				cur_node[c] = {}

			if idx == len(word) - 1:
				cur_node[c]["#"] = {}
			else:
				cur_node = cur_node[c]

	def _searchWord(self, word: str, trie: dict[str, dict]) -> bool:
		cur_node = trie

		for idx, c in enumerate(word):
			if c not in cur_node:
				return False
			else:
				cur_node = cur_node[c]

		if "#" in cur_node:
			return True
		else:
			return False
```