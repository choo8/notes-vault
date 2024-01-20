Given an array of strings `words` and an integer `k`, return _the_ `k` _most frequent strings_.

Return the answer **sorted** by **the frequency** from highest to lowest. Sort the words with the same frequency by their **lexicographical order**.
# Solution Complexity
- $O(nlogk)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
import heapq
from collections import deque

class Solution:
	def topKFrequent(self, words: List[str], k: int) -> List[str]:
		trie = {}

		for w in words:
			cur_node = trie

			for c in w:
				if c not in cur_node:
					cur_node[c] = {}
				cur_node = cur_node[c]

			if "#" not in cur_node:
				cur_node["#"] = (0, w)

			cur_node["#"] = (cur_node["#"][0] - 1, cur_node["#"][1])

		heap, queue = [], deque([trie])

		while len(queue) > 0:
			cur_node = queue.popleft()

			for child in cur_node:
				if child == "#":
					heap.append(cur_node["#"])
				else:
					queue.append(cur_node[child])

		heapq.heapify(heap)

		return [w for _, w in heapq.nsmallest(k, heap)]
```