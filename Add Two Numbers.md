You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
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
	def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
		head, ret, carry = None, None, False

		while l1 is not None or l2 is not None:
			cur_val = 0

			if l1 is not None:
				cur_val += l1.val
				l1 = l1.next

			if l2 is not None:
				cur_val += l2.val
				l2 = l2.next

			if carry:
				cur_val += 1

			if cur_val > 9:
				carry = True
				cur_val = cur_val % 10
			else:
				carry = False

			cur_node = ListNode(cur_val)
			if ret is None:
				head, ret = cur_node, cur_node
			else:
				ret.next = cur_node
				ret = ret.next 

		if carry:
			cur_node = ListNode(1)
			ret.next = cur_node
			ret = ret.next

		return head
```