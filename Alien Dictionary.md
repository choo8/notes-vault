There is a new alien language that uses the English alphabet. However, the order of the letters is unknown to you.

You are given a list of strings `words` from the alien language's dictionary. Now it is claimed that the strings in `words` are **sorted lexicographically** by the rules of this new language.

If this claim is incorrect, and the given arrangement of string in `words` cannot correspond to any order of letters, return `"".`

Otherwise, return _a string of the unique letters in the new alien language sorted in **lexicographically increasing order** by the new language's rules._ If there are multiple solutions, return _**any of them**_.
# Solution Complexity
- $O(nk)$ time complexity
- $O(nk)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

class Solution:
	def alienOrder(self, words: List[str]) -> str:
		char_set = set("".join(words))

		graph = {}
		for c in char_set:
			graph[c] = {"parents": set(), "children": set()}
		for w1, w2 in zip(words, words[1:]):
			min_len = min(len(w1), len(w2))
			if w1[:min_len] == w2[:min_len] and len(w1) > len(w2):
				return ""
			for c1, c2 in zip(w1, w2):
				if c1 != c2:
					graph[c2]["parents"].add(c1)
					graph[c1]["children"].add(c2)
					break

		queue, visited, s = deque([c for c in char_set if len(graph[c]["parents"]) == 0]), set(), []
		while len(queue) > 0:
			cur_c = queue.popleft()

			if cur_c in visited:
				continue
			visited.add(cur_c)
			s.append(cur_c)

			for child in graph[cur_c]["children"]:
				graph[child]["parents"].remove(cur_c)
				if len(graph[child]["parents"]) == 0:
					queue.append(child)

		return "".join(s) if len(visited) == len(char_set) else ""
```