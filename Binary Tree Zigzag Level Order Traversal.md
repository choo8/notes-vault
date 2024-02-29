Given the root of a binary tree, return the zigzag level order traversal of its nodes' values. (i.e., from left to right, then right to left for the next level and alternate between).
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from collections import deque

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def zigzagLevelOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
		if root is None:
			return []

		ret, parents, children, flipped = [[root.val]], deque([root]), deque(), True

		while len(parents) > 0:
			cur_node = parents.popleft()

			if cur_node.left is not None:
				children.append(cur_node.left)

			if cur_node.right is not None:
				children.append(cur_node.right)

			if len(parents) == 0:
				if len(children) == 0:
					break

				if flipped:
					ret.append([node.val for node in reversed(children)])
				else:
					ret.append([node.val for node in children])

				parents, children, flipped = children, deque(), not flipped

		return ret
```