Given the `head` of a singly linked list, group all the nodes with odd indices together followed by the nodes with even indices, and return _the reordered list_.

The **first** node is considered **odd**, and the **second** node is **even**, and so on.

Note that the relative order inside both the even and odd groups should remain as it was in the input.

You must solve the problem in `O(1)` extra space complexity and `O(n)` time complexity.
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
	def oddEvenList(self, head: Optional[ListNode]) -> Optional[ListNode]:
		if head is None or head.next is None:
			return head

		odd, even, even_head = head, head.next, head.next

		while True:
			if even.next is not None and even.next.next is not None:
				odd.next = even.next
				odd = odd.next

				even.next = odd.next
				even = even.next
			elif even.next is not None:
				odd.next = even.next
				odd = even.next

				even.next = None
				break
			else:
				even.next = None
				break

		odd.next = even_head

		return head
```