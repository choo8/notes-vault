A [**trie**](https://en.wikipedia.org/wiki/Trie) (pronounced as "try") or **prefix tree** is a tree data structure used to efficiently store and retrieve keys in a dataset of strings. There are various applications of this data structure, such as autocomplete and spellchecker.

Implement the Trie class:

- `Trie()` Initializes the trie object.
- `void insert(String word)` Inserts the string `word` into the trie.
- `boolean search(String word)` Returns `true` if the string `word` is in the trie (i.e., was inserted before), and `false` otherwise.
- `boolean startsWith(String prefix)` Returns `true` if there is a previously inserted string `word` that has the prefix `prefix`, and `false` otherwise.
# Solution Complexity
- $O(k)$ time complexity for `insert`, `search` and `startsWith`
- $O(nk)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Trie:
	def __init__(self):
		self.trie = {}

	def insert(self, word: str) -> None:
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

		for c in word:
			if c not in cur_node:
				return False
			else:
				cur_node = cur_node[c]

		return "#" in cur_node

	def startsWith(self, prefix: str) -> bool:
		cur_node = self.trie

		for c in prefix:
			if c not in cur_node:
				return False
			else:
				cur_node = cur_node[c]

		return True

# Your Trie object will be instantiated and called as such:
# obj = Trie()
# obj.insert(word)
# param_2 = obj.search(word)
# param_3 = obj.startsWith(prefix)
```