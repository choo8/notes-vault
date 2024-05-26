Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list. Return the linked list sorted as well.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
	def deleteDuplicates(self, head: Optional[ListNode]) -> Optional[ListNode]:
		new_head, prev_node, cur_node = None, None, head

		while cur_node:
			# Current node has a duplicate (next node)
			if cur_node.next and cur_node.val == cur_node.next.val:
				while cur_node.next and cur_node.val == cur_node.next.val:
					cur_node = cur_node.next
				cur_node = cur_node.next

			else:
				if not new_head:
					new_head = cur_node

				if not prev_node:
					prev_node = cur_node
				else:
					prev_node.next = cur_node
					prev_node = cur_node

				cur_node = cur_node.next

		if prev_node:
			prev_node.next = None

		return new_head
```