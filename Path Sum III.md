Given the `root` of a binary tree and an integer `targetSum`, return _the number of paths where the sum of the values along the path equals_ `targetSum`.

The path does not need to start or end at the root or a leaf, but it must go downwards (i.e., traveling only from parent nodes to child nodes).
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def pathSum(self, root: Optional[TreeNode], targetSum: int) -> int:
		self.prefix_sum, self.prefix_sum_dict, self.ret = [], defaultdict(int), 0

		self._dfs(root, targetSum)

		return self.ret

	def _dfs(self, root: Optional[TreeNode], targetSum: int) -> None:
		if root is None:
			return
		else:
			self.prefix_sum.append(self.prefix_sum[-1] + root.val if len(self.prefix_sum) > 0 else root.val)

			if self.prefix_sum[-1] == targetSum:
				self.ret += 1

			if self.prefix_sum[-1] - targetSum in self.prefix_sum_dict:
				self.ret += self.prefix_sum_dict[self.prefix_sum[-1] - targetSum]

			self.prefix_sum_dict[self.prefix_sum[-1]] += 1

			self._dfs(root.left, targetSum)
			self._dfs(root.right, targetSum)

			self.prefix_sum_dict[self.prefix_sum[-1]] -= 1
			self.prefix_sum.pop()

			return
```