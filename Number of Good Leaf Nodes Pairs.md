You are given the `root` of a binary tree and an integer `distance`. A pair of two different **leaf** nodes of a binary tree is said to be good if the length of **the shortest path** between them is less than or equal to `distance`.

Return _the number of good leaf node pairs_ in the tree.
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
	def countPairs(self, root: TreeNode, distance: int) -> int:
		self.num_pairs = 0

		def _postOrderTraversal(self, root: TreeNode) -> List[int]:
			if not root:
				return []
			elif not root.left and not root.right:
				return [1]
			else:
				left = _postOrderTraversal(self, root.left)
				right = _postOrderTraversal(self, root.right)

				for i in left:
					for j in right:
						if i + j <= distance:
							self.num_pairs += 1

				return [d + 1 for d in left + right if d < distance]

		_postOrderTraversal(self, root)

		return self.num_pairs
```