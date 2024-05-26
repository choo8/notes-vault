Given two nodes of a binary tree `p` and `q`, return _their lowest common ancestor (LCA)_.

Each node will have a reference to its parent node. The definition for `Node` is below:
```Java
class Node {
    public int val;
    public Node left;
    public Node right;
    public Node parent;
}
```
According to the **[definition of LCA on Wikipedia](https://en.wikipedia.org/wiki/Lowest_common_ancestor)**: "The lowest common ancestor of two nodes p and q in a tree T is the lowest node that has both p and q as descendants (where we allow **a node to be a descendant of itself**)."
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
    def __init__(self, val):
        self.val = val
        self.left = None
        self.right = None
        self.parent = None
"""

class Solution:
	def lowestCommonAncestor(self, p: 'Node', q: 'Node') -> 'Node':
		ancestors = set()

		cur_p = p
		while cur_p:
			if cur_p.val == q.val:
				return q
			ancestors.add(cur_p.val)
			cur_p = cur_p.parent

		cur_q = q
		while cur_q:
			if cur_q.val in ancestors:
				return cur_q
			cur_q = cur_q.parent

		return None
```