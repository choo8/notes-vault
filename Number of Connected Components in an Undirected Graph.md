You have a graph of `n` nodes. You are given an integer `n` and an array `edges` where `edges[i] = [ai, bi]` indicates that there is an edge between `ai` and `bi` in the graph.

Return _the number of connected components in the graph_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Complexity
# Solution
- asd
```Python
class Solution:
	def countComponents(self, n: int, edges: List[List[int]]) -> int:
		graph = {}
		for i in range(n):
			graph[i] = set()
		for e in edges:
			graph[e[0]].add(e[1])
			graph[e[1]].add(e[0])

		num_components, visited = 0, set(), 
		for i in range(n):
			if i in visited:
				continue
			else:
				num_components += 1

				stack = [i]
				while len(stack) > 0:
					cur_node = stack.pop()

					if cur_node in visited:
						continue
					visited.add(cur_node)

					for child in graph[cur_node]:
						stack.append(child)

		return num_components
```