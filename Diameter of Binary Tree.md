Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.
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
	def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
		self.diameter = 0

		self._helper(root)

		return self.diameter - 1

	def _helper(self, root: Optional[TreeNode]) -> int:
		if root is None:
			return 0
		else:
			left = self._helper(root.left)
			right = self._helper(root.right)

			self.diameter = max(self.diameter, left + right + 1)

			return max(left, right) + 1
```