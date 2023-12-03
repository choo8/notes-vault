Serialization is the process of converting a data structure or object into a sequence of bits so that it can be stored in a file or memory buffer, or transmitted across a network connection link to be reconstructed later in the same or another computer environment.

Design an algorithm to serialize and deserialize a binary tree. There is no restriction on how your serialization/deserialization algorithm should work. You just need to ensure that a binary tree can be serialized to a string and this string can be deserialized to the original tree structure.

**Clarification:** The input/output format is the same as [how LeetCode serializes a binary tree](https://support.leetcode.com/hc/en-us/articles/360011883654-What-does-1-null-2-3-mean-in-binary-tree-representation-). You do not necessarily need to follow this format, so please be creative and come up with different approaches yourself.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adsad
```Python
from collections import deque

# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
class Codec:
	def serialize(self, root):
		"""Encodes a tree to a single string.

		:type root: TreeNode
	    :rtype: str
        """
		queue = deque()
		ret = []

		if root is None:
			return ""

		queue.append(root)
		
		while len(queue) > 0:
			cur_node = queue.popleft()

			if cur_node is not None:
				ret.append(cur_node.val)
			else:
				ret.append(None)

			if cur_node is not None:
				queue.append(cur_node.left)
				queue.append(cur_node.right)

		return ",".join([str(val) for val in ret])

	def deserialize(self, data):
		"""Decodes your encoded data to tree.

		:type data: str
		:rtype: TreeNode
		"""
		queue = deque()

		if data == "":
			return None
		else:
			data = deque([int(val) if val != "None" else None for val in data.split(",")])
			root = TreeNode(data.popleft())
			queue.append(root)

		while len(data) > 0:
			cur_node = queue.popleft()

			left_val, right_val = data.popleft(), data.popleft()
			if left_val is not None:
				cur_node.left = TreeNode(left_val)
				queue.append(cur_node.left)
			if right_val is not None:
				cur_node.right = TreeNode(right_val)
				queue.append(cur_node.right)

		return root

# Your Codec object will be instantiated and called as such:
# ser = Codec()
# deser = Codec()
# ans = deser.deserialize(ser.serialize(root))
```