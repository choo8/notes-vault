Given the `root` of a binary tree, the value of a target node `target`, and an integer `k`, return _an array of the values of all nodes that have a distance_ `k` _from the target node._

You can return the answer in **any order**.
# Solution Complexity
- $O(v + e)$ time complexity
- $O(v + e)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
	def distanceK(self, root: TreeNode, target: TreeNode, k: int) -> List[int]:
		if k == 0:
			return [target.val]

		ret, stack, graph = [], [root], {root.val: set()}
		while len(stack) > 0:
			cur_node = stack.pop()
			
			if cur_node.left:
				graph[cur_node.val].add(cur_node.left.val)
				graph[cur_node.left.val] = {cur_node.val,}
				stack.append(cur_node.left)
			if cur_node.right:
				graph[cur_node.val].add(cur_node.right.val)
				graph[cur_node.right.val] = {cur_node.val,}
				stack.append(cur_node.right)

		parent, children, visited = deque([target.val]), deque(), set()
		while len(parent) > 0:
			cur_node = parent.popleft()

			visited.add(cur_node)

			for child in graph[cur_node]:
				if child not in visited:
					children.append(child)

			if len(parent) == 0:
				if k == 1:
					return [child for child in children]

				parent, children = children, deque()
				k -= 1

		return []
```