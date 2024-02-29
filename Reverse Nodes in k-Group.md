Given the `head` of a linked list, reverse the nodes of the list `k` at a time, and return _the modified list_.

`k` is a positive integer and is less than or equal to the length of the linked list. If the number of nodes is not a multiple of `k` then left-out nodes, in the end, should remain as it is.

You may not alter the values in the list's nodes, only nodes themselves may be changed.
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
	def reverseKGroup(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
		new_head, prev_group_tail, cur_group_head, cur_group_tail = None, None, head, head

		while cur_group_head:
			# Check if there are k nodes to be reversed
			num_nodes = 1
			while cur_group_head.next is not None and num_nodes < k:
				cur_group_head = cur_group_head.next
				num_nodes += 1

			if num_nodes != k:
				if prev_group_tail is not None:
					prev_group_tail.next = cur_group_tail
				break

			# Reverse current k-group
			cur, prev = cur_group_tail, None
			while cur != cur_group_head:
				temp = cur.next
				cur.next = prev
				prev = cur
				cur = temp
			
			# Update new_head if just reversed first group
			if new_head is None:
				new_head = cur_group_head

			# Connect prev_group_tail to cur_group_head
			if prev_group_tail is not None:
				prev_group_tail.next = cur_group_head

			# Update variables to prepare for reversing next k-group
			temp = cur_group_head.next
			cur_group_head.next = prev
			prev_group_tail = cur_group_tail
			cur_group_head, cur_group_tail = temp, temp

		return new_head
```