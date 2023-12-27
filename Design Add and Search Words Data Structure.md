Design a data structure that supports adding new words and finding if a string matches any previously added string.

Implement the `WordDictionary` class:

- `WordDictionary()` Initializes the object.
- `void addWord(word)` Adds `word` to the data structure, it can be matched later.
- `bool search(word)` Returns `true` if there is any string in the data structure that matches `word` or `false` otherwise. `word` may contain dots `'.'` where dots can be matched with any letter.
# Solution Complexity
- $O(k)$ time complexity for `addWord` and $O(nk)$ time complexity for `search`
- $O(nk)$ space complexity
# Thought Process
# Solution
- adasd
```Python
class WordDictionary:
	def __init__(self):
		self.trie = {}

	def addWord(self, word: str) -> None:
		cur_node = self.trie

		for idx, c in enumerate(word):
			if c not in cur_node:
				cur_node[c] = {}

			if idx == len(word) - 1:
				cur_node[c]["#"] = None
			else:
				cur_node = cur_node[c]

	def search(self, word: str) -> bool:
		cur_node = self.trie
		stack = [(0, cur_node)]

		while len(stack) > 0:
			cur_idx, cur_node = stack.pop()

			if cur_idx == len(word):
				continue

			if cur_idx == len(word) - 1:
				if word[cur_idx] == ".":
					for child in cur_node:
						if cur_node[child] is not None and "#" in cur_node[child]:
							return True
				else:
					if word[cur_idx] in cur_node and "#" in cur_node[word[cur_idx]]:
						return True

			if word[cur_idx] == ".":
				for child in cur_node:
					if child != "#":
						stack.append((cur_idx + 1, cur_node[child]))
			else:
				if word[cur_idx] in cur_node:
					stack.append((cur_idx + 1, cur_node[word[cur_idx]]))

		return False

# Your WordDictionary object will be instantiated and called as such:
# obj = WordDictionary()
# obj.addWord(word)
# param_2 = obj.search(word)
```