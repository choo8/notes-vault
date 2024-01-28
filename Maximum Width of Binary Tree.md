Given the `root` of a binary tree, return _the **maximum width** of the given tree_.

The **maximum width** of a tree is the maximum **width** among all levels.

The **width** of one level is defined as the length between the end-nodes (the leftmost and rightmost non-null nodes), where the null nodes between the end-nodes that would be present in a complete binary tree extending down to that level are also counted into the length calculation.

It is **guaranteed** that the answer will in the range of a **32-bit** signed integer.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from collections import deque

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def widthOfBinaryTree(self, root: Optional[TreeNode]) -> int:
		if root is None:
			return 0

		ret, queue, children = 1, deque([(0, root)]), deque()

		while len(queue) > 0:
			cur_idx, cur_node = queue.popleft()

			if cur_node is not None:
				if cur_node.left is not None:
					children.append((2 * cur_idx, cur_node.left))
				if cur_node.right is not None:
					children.append((2 * cur_idx + 1, cur_node.right))

			if len(queue) == 0:
				if len(children) == 0:
					break

				ret = max(ret, children[-1][0] - children[0][0] + 1)
				queue, children = children, queue

		return ret
```