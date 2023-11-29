Given a binary search tree (BST), find the lowest common ancestor (LCA) node of two given nodes in the BST.

According to the [definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor): “The lowest common ancestor is defined between two nodes `p` and `q` as the lowest node in `T` that has both `p` and `q` as descendants (where we allow **a node to be a descendant of itself**).”
# Solution Complexity
- $O(logn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
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
			if p.val < root.val and q.val < root.val:
				return self.lowestCommonAncestor(root.left, p, q)
			elif p.val > root.val and q.val > root.val:
				return self.lowestCommonAncestor(root.right, p, q)
			else:
				return root
```