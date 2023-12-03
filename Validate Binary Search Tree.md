Given the `root` of a binary tree, _determine if it is a valid binary search tree (BST)_.

A **valid BST** is defined as follows:

- The left subtree of a node contains only nodes with keys **less than** the node's key.
- The right subtree of a node contains only nodes with keys **greater than** the node's key.
- Both the left and right subtrees must also be binary search trees.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
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
	def isValidBST(self, root: Optional[TreeNode]) -> bool:
		if root is None or (root.left is None and root.right is None):
			return True
		else:
			left_val, right_val = -sys.maxsize, sys.maxsize
			left, right = root.left, root.right

			while left is not None:
				left_val = max(left_val, left.val)
				left = left.right

			while right is not None:
				right_val = min(right_val, right.val)
				right = right.left

			return left_val < root.val and root.val < right_val and self.isValidBST(root.left) and self.isValidBST(root.right)
```