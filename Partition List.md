Given the `head` of a linked list and a value `x`, partition it such that all nodes **less than** `x` come before nodes **greater than or equal** to `x`.

You should **preserve** the original relative order of the nodes in each of the two partitions.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ time complexity
# Thought Process
# Solution
- asdad
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
	def partition(self, head: Optional[ListNode], x: int) -> Optional[ListNode]:
		left_head, cur_left = None, None
		right_head, prev_right, cur_right = None, None, head

		while cur_right:
			if cur_right.val < x:
				# Remove current node
				if prev_right:
					prev_right.next = cur_right.next

				# Append current node to the end of the left partition
				if not left_head:
					left_head = cur_right
				if cur_left:
					cur_left.next = cur_right
				cur_left = cur_right
			else:
				if not right_head:
					right_head = cur_right
				prev_right = cur_right

			cur_right = cur_right.next

		# Return original head if left partition is empty
		if not left_head:
			return head
		else:
			cur_left.next = right_head
			return left_head
```