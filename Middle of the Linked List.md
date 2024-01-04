Given the head of a singly linked list, return the middle node of the linked list.

If there are two middle nodes, return the second middle node.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
- The naïve solution would be to first obtain the number of nodes in the linked list by walking down the linked list with a pointer, then, in a separate run, obtain the middle node by walking down half the number of nodes. This algorithm would run with a time complexity $O(n)$ and space complexity of $O(1)$
- To improve upon the naïve solution, we can initialize 2 pointers, `slow` and `fast`, and walk down the linked list, but with the `fast` pointer taking 2 steps each time the `slow` pointer takes a step. The main idea is that we no longer need to separately obtain the length of the linked list first in order to find out the position of the middle node
# Solution
- Initialize pointers `slow` and `fast`, and walk down the linked list with `fast` taking 2 steps for each step `slow` takes
- When `fast` reaches the end, return the node `slow` is pointing to
```Python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, val=0, next=None):
#         self.val = val
#         self.next = next
class Solution:
	def middleNode(self, head: Optional[ListNode]) -> Optional[ListNode]:
		slow, fast = head, head

		while fast is not None and fast.next is not None:
			slow, fast = slow.next, fast.next.next

		return slow
```