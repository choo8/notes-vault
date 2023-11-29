Given the `root` of a binary tree, return _the level order traversal of its nodes' values_. (i.e., from left to right, level by level).
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def levelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
		queue = deque()
		res = []

		if root is None:
			return res
		else:
			queue.append(root)

		cur_level = []
		while len(queue) > 0:
			cur_node = queue.popleft()
			cur_level.append(cur_node)

			if len(queue) == 0:
				for node in cur_level:
					if node.left is not None:
						queue.append(node.left)
					if node.right is not None:
						queue.append(node.right)
				if len(cur_level) != 0:
					res.append([node.val for node in cur_level])
					cur_level = []
				else:
					break

		return res
```