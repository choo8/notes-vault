Given the `root` of a binary tree and an integer `targetSum`, return _all **root-to-leaf** paths where the sum of the node values in the path equals_ `targetSum`_. Each path should be returned as a list of the node **values**, not node references_.

A **root-to-leaf** path is a path starting from the root and ending at any leaf node. A **leaf** is a node with no children.
# Solution Complexity
- $O(n)$ time complexity
- $O((logn)^2)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def pathSum(self, root: Optional[TreeNode], targetSum: int) -> List[List[int]]:
		if root is None:
			return []
		elif root.left is None and root.right is None:
			return [[root.val]] if root.val == targetSum else []
		else:
			left = self.pathSum(root.left, targetSum - root.val)
			right = self.pathSum(root.right, targetSum - root.val)

			return [[root.val] + path for path in left + right]
```