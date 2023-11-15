You are given an array of `k` linked-lists `lists`, each linked-list is sorted in ascending order.

_Merge all the linked-lists into one sorted linked-list and return it._
# Solution Complexity
- $O(kn log(kn))$ time complexity
- $O(kn)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
import heapq

# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
	def mergeKLists(self, lists: List[Optional[ListNode]]) -> Optional[ListNode]:
		heap = []
		head, prev = None, None

		for l in lists:
			while l:
				heapq.heappush(heap, l.val)
				l = l.next

		while heap:
			cur_val = heapq.heappop(heap)
			
			if not head:
				head = ListNode(cur_val)
				prev = head
			else:
				cur = ListNode(cur_val)
				prev.next = cur
				prev = cur

		return head
```