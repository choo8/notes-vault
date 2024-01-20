A tree is an undirected graph in which any two vertices are connected by _exactly_ one path. In other words, any connected graph without simple cycles is a tree.

Given a tree of `n` nodes labelled from `0` to `n - 1`, and an array of `n - 1` `edges` where `edges[i] = [ai, bi]` indicates that there is an undirected edge between the two nodes `ai` and `bi` in the tree, you can choose any node of the tree as the root. When you select a node `x` as the root, the result tree has height `h`. Among all possible rooted trees, those with minimum height (i.e. `min(h)`)  are called **minimum height trees** (MHTs).

Return _a list of all **MHTs'** root labels_. You can return the answer in **any order**.

The **height** of a rooted tree is the number of edges on the longest downward path between the root and a leaf.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict, deque

class Solution:
	def findMinHeightTrees(self, n: int, edges: List[List[int]]) -> List[int]:
		if n < 2:
			return [n for n in range(n)]

		adj_list = defaultdict(set)

		for v1, v2 in edges:
			adj_list[v1].add(v2)
			adj_list[v2].add(v1)

		leaves = [n for n in adj_list if len(adj_list[n]) == 1]

		while n > 2:
			children = []

			for leaf in leaves:
				n -= 1

				for neighbor in adj_list[leaf]:
					adj_list[neighbor].remove(leaf)

					if len(adj_list[neighbor]) == 1:
						children.append(neighbor)

			leaves = children

		return leaves
```