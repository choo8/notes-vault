Given the `head` of a linked list, return _the list after sorting it in **ascending order**_.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(1)$ space complexity
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
	def sortList(self, head: Optional[ListNode]) -> Optional[ListNode]:
		if head is None or head.next is None:
			return head
		else:
			slow, fast = head, head

			while fast.next is not None and fast.next.next is not None:
				slow, fast = slow.next, fast.next.next

			left, right = head, slow.next
			slow.next = None

			ret, cur_node, left, right = None, None, self.sortList(left), self.sortList(right)

			while left is not None or right is not None:
				if left is None:
					if cur_node is None:
						ret, cur_node = right, right
					else:
						cur_node.next = right
						cur_node = cur_node.next
					right = right.next
				elif right is None:
					if cur_node is None:
						ret, cur_node = left, left
					else:
						cur_node.next = left
						cur_node = cur_node.next
					left = left.next
				else:
					if left.val <= right.val:
						if cur_node is None:
							ret, cur_node = left, left
						else:
							cur_node.next = left
							cur_node = cur_node.next
						left = left.next
					else:
						if cur_node is None:
							ret, cur_node = right, right
						else:
							cur_node.next = right
							cur_node = cur_node.next
						right = right.next

			return ret
```