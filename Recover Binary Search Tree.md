You are given the `root` of a binary search tree (BST), where the values of **exactly** two nodes of the tree were swapped by mistake. _Recover the tree without changing its structure_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def recoverTree(self, root: Optional[TreeNode]) -> None:
		"""
		Do not return anything, modify root in-place instead.
		"""

		inorder_nodes = self._inorderTraversal(root)
		left = 0
		while True:
			if inorder_nodes[left].val > inorder_nodes[left + 1].val or (left - 1 >= 0 and inorder_nodes[left - 1].val > inorder_nodes[left].val):
				break
			left += 1

		right = len(inorder_nodes) - 1
		while True:
			if inorder_nodes[right - 1].val > inorder_nodes[right].val or (right + 1 < len(inorder_nodes) and inorder_nodes[right - 1].val > inorder_nodes[right].val):
				break
			right -= 1

		inorder_nodes[left].val, inorder_nodes[right].val = inorder_nodes[right].val, inorder_nodes[left].val

	def _inorderTraversal(self, root: Optional[TreeNode]) -> List[TreeNode]:
		if not root:
			return []
		else:
			return self._inorderTraversal(root.left) + [root] + self._inorderTraversal(root.right)
```