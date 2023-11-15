Given a string `s` containing just the characters `'('`, `')'`, `'{'`, `'}'`, `'['` and `']'`, determine if the input string is valid.

An input string is valid if:

1. Open brackets must be closed by the same type of brackets.
2. Open brackets must be closed in the correct order.
3. Every close bracket has a corresponding open bracket of the same type.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adasd
```Python
class Solution:
	def isValid(self, s: str) -> bool:
		stack = []
		bracket_dict = {"(": ")", "{": "}", "[": "]"}

		for c in s:
			if c in ["(", "{", "["]:
				stack.append(c)
			else:
				if len(stack) == 0 or bracket_dict[stack.pop()] != c:
					return False

		return len(stack) == 0
```