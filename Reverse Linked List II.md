Given the `head` of a singly linked list and two integers `left` and `right` where `left <= right`, reverse the nodes of the list from position `left` to position `right`, and return _the reversed list_.
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
	def reverseBetween(self, head: Optional[ListNode], left: int, right: int) -> Optional[ListNode]:
		# No reversing to be done
		if left == right:
			return head

		# Get pointers to left and right nodes
		prev_left, cur_left = None, head
		for _ in range(left - 1):
			prev_left = cur_left
			cur_left = cur_left.next

		cur_right = cur_left
		for _ in range(right - left):
			cur_right = cur_right.next

		if not prev_left:
			head = cur_right

		for _ in range(right - left):
			# Remove node
			removed_node = cur_left
			if prev_left:
				prev_left.next = cur_left.next
			cur_left = cur_left.next

			# Insert node back into linked list
			rest = cur_right.next
			cur_right.next = removed_node
			removed_node.next = rest

		return head
```