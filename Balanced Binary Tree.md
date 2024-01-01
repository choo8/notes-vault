Given a binary tree, determine if it is **height-balanced**.
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
	def isBalanced(self, root: Optional[TreeNode]) -> bool:
		self.balanced = True

		self._helper(root)

		return self.balanced

	def _helper(self, root: Optional[TreeNode]) -> int:
		if root is None:
			return 0
		left = self._helper(root.left)
		right = self._helper(root.right)

		if abs(left - right) > 1:
			self.balanced = False

		return max(left, right) + 1
```