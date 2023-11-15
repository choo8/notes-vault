You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one **sorted** list. The list should be made by splicing together the nodes of the first two lists.

Return _the head of the merged linked list_.
# Solution Complexity
- $O(m + n)$ time complexity
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
	def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:
		head = None
		prev = None

		while list1 and list2:
			if list1.val < list2.val:
				if not head:
					head = list1
					prev = list1
				else:
					prev.next = list1
					prev = list1
				list1 = list1.next
			else:
				if not head:
					head = list2
					prev = list2
				else:
					prev.next = list2
					prev = list2
				list2 = list2.next

		if list1:
			if prev:
				prev.next = list1
			else:
				head = list1

		if list2:
			if prev:
				prev.next = list2
			else:
				head = list2

		return head
```