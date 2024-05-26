A parentheses string is valid if and only if:

- It is the empty string,
- It can be written as `AB` (`A` concatenated with `B`), where `A` and `B` are valid strings, or
- It can be written as `(A)`, where `A` is a valid string.

You are given a parentheses string `s`. In one move, you can insert a parenthesis at any position of the string.

- For example, if `s = "()))"`, you can insert an opening parenthesis to be `"(**(**)))"` or a closing parenthesis to be `"())**)**)"`.

Return _the minimum number of moves required to make_ `s` _valid_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def minAddToMakeValid(self, s: str) -> int:
		stack, num_add = [], 0	
		for c in s:
			if c == "(":
				stack.append(c)
			else:
				if len(stack) > 0:
					stack.pop()
				else:
					num_add += 1
		return num_add + len(stack)
```