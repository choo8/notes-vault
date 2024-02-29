Given the `head` of a linked list, rotate the list to the right by `k` places.
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
	def rotateRight(self, head: Optional[ListNode], k: int) -> Optional[ListNode]:
		if head is None:
			return head

		last_node, cur_node, list_len = None, head, 0
		while cur_node is not None:
			last_node = cur_node
			cur_node = cur_node.next
			list_len += 1

		k = k % list_len

		if k == 0:
			return head

		prev, new_head = None, head
		for _ in range(list_len - k):
			prev = new_head
			new_head = new_head.next

		last_node.next = head
		if prev is not None:
			prev.next = None

		return new_head
```