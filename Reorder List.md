You are given the head of a singly linked-list. The list can be represented as:

L0 → L1 → … → Ln - 1 → Ln

_Reorder the list to be on the following form:_

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …

You may not modify the values in the list's nodes. Only nodes themselves may be changed.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
	def reorderList(self, head: Optional[ListNode]) -> None:
		stack = []
		cur, cur_next, end = head, None, None

		while cur:
			stack.append(cur)
			cur = cur.next

		cur = head
		num_nodes = len(stack)

		for _ in range(num_nodes // 2):
			end = stack.pop()
			cur_next = cur.next
			cur.next, end.next = end, cur.next

			cur = cur_next

		if num_nodes % 2 == 1 and cur_next:
			end.next = cur_next
			cur_next.next = None
		elif end:
			end.next = None
```