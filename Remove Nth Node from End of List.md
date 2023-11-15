Given the head of a linked list, remove the nth node from the end of the list and return its head.
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
	def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
		prev = None
		cur, end = head, head

		for _ in range(n):
			end = end.next

		while end:
			prev = cur
			cur = cur.next
			end = end.next

		if not prev:
			head = head.next
		else:
			prev.next = cur.next

		return head
```