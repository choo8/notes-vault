Given a string s of `'('` , `')'` and lowercase English characters.

Your task is to remove the minimum number of parentheses ( `'('` or `')'`, in any positions ) so that the resulting _parentheses string_ is valid and return **any** valid string.

Formally, a _parentheses string_ is valid if and only if:

- It is the empty string, contains only lowercase characters, or
- It can be written as `AB` (`A` concatenated with `B`), where `A` and `B` are valid strings, or
- It can be written as `(A)`, where `A` is a valid string.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def minRemoveToMakeValid(self, s: str) -> str:
		stack, removed_str = [], []
		for c in s:
			if c == "(":
				stack.append(c)
				removed_str.append(c)
			elif c == ")":
				if len(stack) > 0:
					stack.pop()
					removed_str.append(c)
			else:
				removed_str.append(c)

		# Remove remaining "("
		new_stack = []
		while len(stack) > 0:
			if removed_str[-1] == "(":
				stack.pop()
				removed_str.pop()
			else:
				new_stack.append(removed_str.pop())
		while len(new_stack) > 0:
			removed_str.append(new_stack.pop())

		return "".join(removed_str)
```