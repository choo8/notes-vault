A phrase is a **palindrome** if, after converting all uppercase letters into lowercase letters and removing all non-alphanumeric characters, it reads the same forward and backward. Alphanumeric characters include letters and numbers.

Given a string `s`, return `true` _if it is a **palindrome**, or_ `false` _otherwise_.
# Solution Complexity
# Thought Process
# Solution
- asdfsdafsdf
```Python
class Solution:
	def isPalindrome(self, s: str) -> bool:
		filtered_s = "".join(c for c in s if c.isalnum())
		left, right = 0, len(filtered_s) - 1

		while left < right:
			if filtered_s[left].lower() != filtered_s[right].lower():
				return False

			left += 1
			right -= 1

		return True
```