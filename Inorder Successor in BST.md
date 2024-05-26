Given the `root` of a binary search tree and a node `p` in it, return _the in-order successor of that node in the BST_. If the given node has no in-order successor in the tree, return `null`.

The successor of a node `p` is the node with the smallest key greater than `p.val`.
# Solution Complexity
- $O(n)$ time complexity
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
	def inorderSuccessor(self, root: TreeNode, p: TreeNode) -> Optional[TreeNode]:
		cur_node, left, right = root, None, None

		while cur_node:
			if cur_node == p:
				if not cur_node.right:
					return right
				
				left_most = cur_node.right
				while left_most.left:
					left_most = left_most.left
				return left_most
			elif cur_node.val < p.val:
				left = cur_node
				cur_node = cur_node.right
			else:
				right = cur_node
				cur_node = cur_node.left
```