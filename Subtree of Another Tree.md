Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.
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
	def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
		if root is None:
			return subRoot is None
		else:
			res = False
			
			if root.left is not None:
				res = res or self.isSubtree(root.left, subRoot)
			if root.right is not None:
				res = res or self.isSubtree(root.right, subRoot)
			if subRoot is not None and root.val == subRoot.val:
				res = res or (self.isTree(root.left, subRoot.left) and self.isTree(root.right, subRoot.right))

			return res

	def isTree(self, r1: Optional[TreeNode], r2: Optional[TreeNode]) -> bool:
		if r1 is None and r2 is None:
			return True
		elif r1 is not None and r2 is not None:
			return r1.val == r2.val and self.isTree(r1.left, r2.left) and self.isTree(r1.right, r2.right)
		else:
			return False
```