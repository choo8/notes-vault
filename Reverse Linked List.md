Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ time complexity
# Thought Process
# Solution
- adasd
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
	def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
		new_head = None
		cur, prev = head, None

		while cur:
			tmp = cur.next
			cur.next = prev
			prev = cur
			new_head = cur
			cur = tmp

		return new_head
```