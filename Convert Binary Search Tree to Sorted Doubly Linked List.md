Convert a **Binary Search Tree** to a sorted **Circular Doubly-Linked List** in place.

You can think of the left and right pointers as synonymous to the predecessor and successor pointers in a doubly-linked list. For a circular doubly linked list, the predecessor of the first element is the last element, and the successor of the last element is the first element.

We want to do the transformation **in place**. After the transformation, the left pointer of the tree node should point to its predecessor, and the right pointer should point to its successor. You should return the pointer to the smallest element of the linked list.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asad
```Python
"""
# Definition for a Node.
class Node:
    def __init__(self, val, left=None, right=None):
        self.val = val
        self.left = left
        self.right = right
"""

class Solution:
	def treeToDoublyList(self, root: 'Optional[Node]') -> 'Optional[Node]':
		if not root:
			return root
		elif not root.left and not root.right:
			root.left, root.right = root, root
			return root
		else:
			stack, visited = [root], set()
			prev_node = Node()
			head = prev_node

			# inorder traversal of tree
			while len(stack) > 0:
				if stack[-1].left and stack[-1].left not in visited:
					stack.append(stack[-1].left)
					continue

				cur_node = stack.pop()
				visited.add(cur_node)

				if cur_node.right:
					stack.append(cur_node.right)

				prev_node.right = cur_node
				cur_node.left = prev_node
				prev_node = cur_node

			head.right.left = cur_node
			cur_node.right = head.right

			return head.next
```