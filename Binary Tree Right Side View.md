Given the `root` of a binary tree, imagine yourself standing on the **right side** of it, return _the values of the nodes you can see ordered from top to bottom_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adsad
```Python
from collections import deque

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def rightSideView(self, root: Optional[TreeNode]) -> List[int]:
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
				res.append(cur_level[-1].val)
				cur_level = []

		return res
```