You are given the `root` of a binary tree containing digits from `0` to `9` only.

Each root-to-leaf path in the tree represents a number.

- For example, the root-to-leaf path `1 -> 2 -> 3` represents the number `123`.

Return _the total sum of all root-to-leaf numbers_. Test cases are generated so that the answer will fit in a **32-bit** integer.

A **leaf** node is a node with no children.
# Solution Complexity
- $O(n)$ time complexity
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
	def sumNumbers(self, root: Optional[TreeNode]) -> int:
		return self._helper(root, 0)

	def _helper(self, root: Optional[TreeNode], cur_sum: int) -> int:
		if not root:
			return cur_sum
		elif not root.left and not root.right:
			return cur_sum * 10 + root.val
		else:
			ret = 0
			if root.left:
				ret += self._helper(root.left, cur_sum * 10 + root.val)
			if root.right:
				ret += self._helper(root.right, cur_sum * 10 + root.val)
			return ret
```