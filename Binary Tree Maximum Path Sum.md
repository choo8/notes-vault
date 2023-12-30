A **path** in a binary tree is a sequence of nodes where each pair of adjacent nodes in the sequence has an edge connecting them. A node can only appear in the sequence **at most once**. Note that the path does not need to pass through the root.

The **path sum** of a path is the sum of the node's values in the path.

Given the `root` of a binary tree, return _the maximum **path sum** of any **non-empty** path_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
import sys

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def maxPathSum(self, root: Optional[TreeNode]) -> int:
		self.maxPath = -sys.maxsize

		self._helper(root)

		return self.maxPath

	def _helper(self, root: Optional[TreeNode]) -> int:
		if root is None:
			return 0
		else:
			left = self._helper(root.left)
			right = self._helper(root.right)

			self.maxPath = max(self.maxPath, root.val, root.val + left + right)

			return max(root.val + max(left, right), 0)
```