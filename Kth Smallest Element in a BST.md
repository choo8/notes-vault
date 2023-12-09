Given the root of a binary search tree, and an integer k, return the kth smallest value (1-indexed) of all the values of the nodes in the tree.
# Solution Complexity
- $O(logn)$ time complexity
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
	def kthSmallest(self, root: Optional[TreeNode], k: int) -> int:
		if k == self.treeSize(root.left) + 1:
			return root.val
		elif k <= self.treeSize(root.left):
			return self.kthSmallest(root.left, k)
		else:
			return self.kthSmallest(root.right, k - self.treeSize(root.left) - 1)

	def treeSize(self, root: Optional[TreeNode]) -> int:
		if root is None:
			return 0
		if root.left is None and root.right is None:
			return 1
		else:
			return 1 + self.treeSize(root.left) + self.treeSize(root.right)
```