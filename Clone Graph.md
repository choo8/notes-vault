Given a reference of a node in a **[connected](https://en.wikipedia.org/wiki/Connectivity_(graph_theory)#Connected_graph)** undirected graph.

Return a [**deep copy**](https://en.wikipedia.org/wiki/Object_copying#Deep_copy) (clone) of the graph.

Each node in the graph contains a value (`int`) and a list (`List[Node]`) of its neighbors.
```Java
class Node {
    public int val;
    public List<Node> neighbors;
}
```
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- adasd
```Python
from collections import deque

"""
# Definition for a Node.
class Node:
    def __init__(self, val = 0, neighbors = None):
        self.val = val
        self.neighbors = neighbors if neighbors is not None else []
"""
class Solution:
	def cloneGraph(self, node: 'Node') -> 'Node':
		if node is None:
			return None
		else:
			ret_val = node.val
			new_nodes = [None] * 101

			queue = deque()
			queue.append(node)

			while len(queue) > 0:
				cur_node = queue.popleft()

				if new_nodes[cur_node.val] is None:
					new_nodes[cur_node.val] = Node(cur_node.val)

				for neighbor in cur_node.neighbors:
					if new_nodes[neighbor.val] is None:
						queue.append(neighbor)
						new_nodes[neighbor.val] = Node(neighbor.val)

					new_nodes[cur_node.val].neighbors.append(new_nodes[neighbor.val])

		return new_nodes[ret_val]
```