Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def maxDepth(self, root: Optional[TreeNode]) -> int:
		if root is None:
			return 0
		elif root.left is None:
			return 1 + self.maxDepth(root.right)
		elif root.right is None:
			return 1 + self.maxDepth(root.left)
		else:
			return 1 + max(self.maxDepth(root.left), self.maxDepth(root.right))
```