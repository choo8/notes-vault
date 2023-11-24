Given a string `s` representing a valid expression, implement a basic calculator to evaluate it, and return _the result of the evaluation_.

**Note:** You are **not** allowed to use any built-in function which evaluates strings as mathematical expressions, such as `eval()`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- dasd
```Python
class Solution:
	def calculate(self, s: str) -> int:
		stack = []
		s_stripped = "(" + "".join(s.split(" ")) + ")"

		for c in s_stripped:
			if c == ")":
				res = 0

				while stack[-1] != "(":
					operand = ""

					while stack[-1] not in ["(", "+", "-"]:
						operand = stack.pop() + operand

					if stack[-1] in ["+", "-"]:
						operator = stack.pop()

						if operator == "+":
							res += int(operand)
						elif operator == "-":
							res -= int(operand)
					else:
						res += int(operand)

				stack.pop()
				stack.append(str(res))
			else:
				stack.append(c)

		return int(stack[-1])
```