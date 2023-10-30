Given a string containing digits from `2-9` inclusive, return all possible letter combinations that the number could represent. Return the answer in **any order**.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.
# Solution Complexity
- $O()$
# Thought Process
# Solution
- adad
```Python
digits_map = {
	"2": "abc",
	"3": "def",
	"4": "ghi",
	"5": "jkl",
	"6": "mno",
	"7": "pqrs",
	"8": "tuv",
	"9": "wxyz"
}

class Solution:
	def letterCombinations(self, digits: str) -> List[str]:
		self.digits = digits
		self.res = []

		self._combinations(0, "")

		return self.res

	def _combinations(self, idx: int, cur: str) -> None:
		if idx == len(self.digits):
			if cur != "":
				self.res.append(cur)
			return

		for c in digits_map[self.digits[idx]]:
			self._combinations(idx + 1, cur + c)
```