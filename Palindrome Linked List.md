Given the `head` of a singly linked list, return `true` _if it is a palindrome or `false` otherwise_.
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
	def isPalindrome(self, head: Optional[ListNode]) -> bool:
		if head is None or head.next is None:
			return True
		
		slow, fast = head, head
		reversed_head = None

		while fast is not None and fast.next is not None:
			tmp = slow
			slow = slow.next
			fast = fast.next.next

			tmp.next = reversed_head
			reversed_head = tmp

		if fast is not None:
			slow = slow.next

		while slow is not None and reversed_head is not None:
			if reversed_head.val != slow.val:
				return False
			else:
				reversed_head = reversed_head.next
				slow = slow.next

		return True
```