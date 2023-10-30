Given `n` pairs of parentheses, write a function to _generate all combinations of well-formed parentheses_.
# Solution Complexity
- $O(2^n)$ time complexity
- $O()$
# Thought Process
- asdasdasd
# Solution
- adasd
```Python
class Solution:
	def generateParenthesis(self, n: int) -> List[str]:
		self.parentheses = []
		self._generate(n, 0, 0, "")

		return self.parentheses

	def _generate(self, n: int, left: int, right: int, cur: str) -> List[str]:
		if left == n and right == n:
			self.parentheses.append(cur)

		if left < n:
			self._generate(n, left + 1, right, cur + "(")

		if right < left:
			self._generate(n, left, right + 1, cur + ")")
```