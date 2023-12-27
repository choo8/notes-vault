Given a binary tree, find the lowest common ancestor (LCA) of two given nodes in the tree.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Solution:
	def lowestCommonAncestor(self, root: 'TreeNode', p: 'TreeNode', q: 'TreeNode') -> 'TreeNode':
		if root is None:
			return None
		else:
			left = self.lowestCommonAncestor(root.left, p, q)
			right = self.lowestCommonAncestor(root.right, p, q)

			if left is not None and right is not None:
				if (left.val == p.val and right.val == q.val) or (left.val == q.val and right.val == p.val):
					return root
			elif left is not None:
				if (left.val == p.val and root.val == q.val) or (left.val == q.val and root.val == p.val):
					return root
				else:
					return left
			elif right is not None:
				if (right.val == p.val and root.val == q.val) or (right.val == q.val and root.val == p.val):
					return root
				else:
					return right
			else:
				return root if root.val == p.val or root.val == q.val else None
```