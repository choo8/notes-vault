Given the `root` of a binary tree, return _**the vertical order traversal** of its nodes' values_. (i.e., from top to bottom, column by column).

If two nodes are in the same row and column, the order should be from **left to right**.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
from collections import deque, defaultdict

# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
	def verticalOrder(self, root: Optional[TreeNode]) -> List[List[int]]:
		if not root:
			return []
			
		col_dict, columns = defaultdict(list), []
		left, right = 0, 0

		visited = set()
		queue = deque([(0, root)])
		while len(queue) > 0:
			col, cur_node = queue.popleft()

			col_dict[col].append(cur_node.val)

			if cur_node.left:
				queue.append((col - 1, cur_node.left))
				left = min(left, col - 1)
			if cur_node.right:
				queue.append((col + 1, cur_node.right))
				right = max(right, col + 1)

		for col in range(left, right + 1):
			if col_dict[col]:
				columns.append(col_dict[col])

		return columns
```