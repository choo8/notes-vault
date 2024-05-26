You have a graph of `n` nodes labeled from `0` to `n - 1`. You are given an integer n and a list of `edges` where `edges[i] = [ai, bi]` indicates that there is an undirected edge between nodes `ai` and `bi` in the graph.

Return `true` _if the edges of the given graph make up a valid tree, and_ `false` _otherwise_.
# Solution Complexity
- $O(V + E)$ time complexity
- $O(V + E)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def validTree(self, n: int, edges: List[List[int]]) -> bool:
		# Create graph
		graph = {}
		for i in range(n):
			graph[i] = set()
		for e in edges:
			graph[e[0]].add(e[1])
			graph[e[1]].add(e[0])

		# DFS to traverse graph
		visited_nodes, parent, stack = set(), {}, [0]
		while len(stack) > 0:
			cur_node = stack.pop()

			if cur_node in visited_nodes:
				return False
			visited_nodes.add(cur_node)

			for child in graph[cur_node]:
				if cur_node in parent and parent[cur_node] == child:
					continue
				parent[child] = cur_node
				stack.append(child)

		return len(visited_nodes) == n
```