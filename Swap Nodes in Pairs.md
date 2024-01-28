Given a linked list, swap every two adjacent nodes and return its head. You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed.)
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
	def swapPairs(self, head: Optional[ListNode]) -> Optional[ListNode]:
		if head is None or head.next is None:
			return head
		else:
			temp = head.next
			head.next = self.swapPairs(temp.next)
			temp.next = head
			return temp
```