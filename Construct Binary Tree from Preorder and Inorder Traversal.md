Given two integer arrays `preorder` and `inorder` where `preorder` is the preorder traversal of a binary tree and `inorder` is the inorder traversal of the same tree, construct and return _the binary tree_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- adsad
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def buildTree(self, preorder: List[int], inorder: List[int]) -> Optional[TreeNode]:
		if preorder == [] and inorder == []:
			return None
		else:
			root, root_idx = TreeNode(preorder[0]), inorder.index(preorder[0])
			num_left = len(inorder[:root_idx])
			root.left = self.buildTree(preorder[1:num_left + 1], inorder[:root_idx])
			root.right = self.buildTree(preorder[num_left + 1:], inorder[root_idx + 1:])
			return root
```