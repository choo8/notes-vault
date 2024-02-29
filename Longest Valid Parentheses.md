Given a string containing just the characters `'('` and `')'`, return _the length of the longest valid (well-formed) parentheses substring_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def longestValidParentheses(self, s: str) -> int:
		stack, max_length = [-1], 0

		for idx, c in enumerate(s):
			if c == "(":
				stack.append(idx)
			else:
				stack.pop()
				if len(stack) == 0:
					stack.append(idx)
				else:
					max_length = max(max_length, idx - stack[-1])

		return max_length
```