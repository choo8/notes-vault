A **transformation sequence** from word `beginWord` to word `endWord` using a dictionary `wordList` is a sequence of words `beginWord -> s1 -> s2 -> ... -> sk` such that:

- Every adjacent pair of words differs by a single letter.
- Every `si` for `1 <= i <= k` is in `wordList`. Note that `beginWord` does not need to be in `wordList`.
- `sk == endWord`

Given two words, `beginWord` and `endWord`, and a dictionary `wordList`, return _the **number of words** in the **shortest transformation sequence** from_ `beginWord` _to_ `endWord`_, or_ `0` _if no such sequence exists._
# Solution Complexity
- $O(nk)$ time complexity
- $O(nk)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from collections import deque

class Solution:
	def ladderLength(self, beginWord: str, endWord: str, wordList: List[str]) -> int:
		if endWord not in wordList:
			return 0

		graph = {}
		for word in [beginWord] + wordList:
			for idx in range(len(word)):
				key = (idx, word[:idx] + word[idx + 1:])
				if key not in graph:
					graph[key] = set()
				graph[key].add(word)

		visited, parents, children, num_words = set([beginWord]), deque([beginWord]), deque(), 1
		while len(parents) > 0:
			if num_words > len(wordList) + 1:
				return 0

			cur_word = parents.popleft()

			if cur_word == endWord:
				return num_words

			for idx in range(len(cur_word)):
				key = (idx, cur_word[:idx] + cur_word[idx + 1:])
				if key not in graph:
					continue
				for child in graph[key]:
					if child not in visited and child not in children:
						children.append(child)
						visited.add(child)
	
			if len(parents) == 0:
				parents, children = children, deque()
				num_words += 1

		return 0
```