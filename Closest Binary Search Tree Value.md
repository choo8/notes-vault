Given the `root` of a binary search tree and a `target` value, return _the value in the BST that is closest to the_ `target`. If there are multiple answers, print the smallest.
# Solution Complexity
- $O(logn)$ time complexity
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
	def closestValue(self, root: Optional[TreeNode], target: float) -> int:
		self.closest = sys.maxsize
		self._search(root, target)
		return self.closest

	def _search(self, root: Optional[TreeNode], target: float) -> None:
		if not root:
			return
		else:
			if abs(root.val - target) < abs(self.closest - target) or (abs(root.val - target) == abs(self.closest - target) and root.val < self.closest):
				self.closest = root.val

			if target < root.val:
				self._search(root.left, target)
			else:
				self._search(root.right, target)
```