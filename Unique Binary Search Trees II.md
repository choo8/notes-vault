Given an integer `n`, return _all the structurally unique **BST**'s (binary search trees), which has exactly_ `n` _nodes of unique values from_ `1` _to_ `n`. Return the answer in **any order**.
# Solution Complexity
- $O(\frac{4^n}{n\sqrt{n}})$ time complexity
- $O(\frac{4^n}{n\sqrt{n}})$ space complexity
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
	def generateTrees(self, n: int) -> List[Optional[TreeNode]]:
		dp = [[] for _ in range(n + 1)]
		dp[0].append(None)

		for num_nodes in range(1, n + 1):
			for root in range(1, n + 1):
				for left_child in dp[root - 1]:
					for right_child in dp[num_nodes - root]:
						cur_root = TreeNode(root)
						cur_root.left = self._copyTree(left_child, 0)
						cur_root.right = self._copyTree(right_child, root)
						dp[num_nodes].append(cur_root)

		return dp[n]

	def _copyTree(self, root: Optional[TreeNode], offset: int) -> Optional[TreeNode]:
		if not root:
			return None
		else:
			new_root = TreeNode(root.val + offset)
			new_root.left = self._copyTree(root.left, offset)
			new_root.right = self._copyTree(root.right, offset)
			return new_root
```
