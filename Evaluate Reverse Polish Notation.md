You are given an array of strings `tokens` that represents an arithmetic expression in a [Reverse Polish Notation](http://en.wikipedia.org/wiki/Reverse_Polish_notation).

Evaluate the expression. Return _an integer that represents the value of the expression_.

**Note** that:

- The valid operators are `'+'`, `'-'`, `'*'`, and `'/'`.
- Each operand may be an integer or another expression.
- The division between two integers always **truncates toward zero**.
- There will not be any division by zero.
- The input represents a valid arithmetic expression in a reverse polish notation.
- The answer and all the intermediate calculations can be represented in a **32-bit** integer.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def evalRPN(self, tokens: List[str]) -> int:
		stack = []
		operators = ["+", "-", "*", "/"]

		for t in tokens:
			if t not in operators:
				stack.append(int(t))
			else:
				second, first = stack.pop(), stack.pop()
				
				if t == "+":
					stack.append(first + second)
				elif t == "-":
					stack.append(first - second)
				elif t == "*":
					stack.append(first * second)
				else:
					stack.append(int(first / second))

		return stack[-1]
```