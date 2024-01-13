Given the `root` of a binary tree, _check whether it is a mirror of itself_ (i.e., symmetric around its center).
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- ads
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def isSymmetric(self, root: Optional[TreeNode]) -> bool:
		if root is None:
			return True

		return self._helper(root.left, root.right)

	def _helper(self, root1: Optional[TreeNode], root2: Optional[TreeNode]) -> bool:
		if root1 is None and root2 is None:
			return True
		elif root1 is None or root2 is None:
			return False
		else:
			return root1.val == root2.val and self._helper(root1.right, root2.left) and self._helper(root1.left, root2.right)
```