Given a Circular Linked List node, which is sorted in non-descending order, write a function to insert a value `insertVal` into the list such that it remains a sorted circular list. The given node can be a reference to any single node in the list and may not necessarily be the smallest value in the circular list.

If there are multiple suitable places for insertion, you may choose any place to insert the new value. After the insertion, the circular list should remain sorted.

If the list is empty (i.e., the given node is `null`), you should create a new single circular list and return the reference to that single node. Otherwise, you should return the originally given node.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
"""
# Definition for a Node.
class Node:
    def __init__(self, val=None, next=None):
        self.val = val
        self.next = next
"""

class Solution:
	def insert(self, head: 'Optional[Node]', insertVal: int) -> 'Node':
		# Empty linked list
		if not head:
			head = Node(insertVal)
			head.next = head
		# Only one node in linked list
		elif head.next == head:
			cur_node = Node(insertVal)
			
			head.next = cur_node
			cur_node.next = head
		else:
			cur_node, moved, inserted = head, False, False

			while cur_node != head or not moved:
				# Insert new node here
				if (insertVal >= cur_node.val and (insertVal <= cur_node.next.val or cur_node.next.val < cur_node.val)) or (insertVal < cur_node.val and insertVal < cur_node.next.val and cur_node.next.val < cur_node.val):
					new_node = Node(insertVal)
					temp = cur_node.next
					cur_node.next = new_node
					new_node.next = temp
					inserted = True
					break
				moved = True
				cur_node = cur_node.next

			if not inserted:
				new_node = Node(insertVal)
				temp = cur_node.next
				cur_node.next = new_node
				new_node.next = temp

		return head
```