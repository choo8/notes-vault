Given a string `s`, return `true` _if the_ `s` _can be palindrome after deleting **at most one** character from it_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def validPalindrome(self, s: str) -> bool:
		left, right = 0, len(s) - 1

		while left < right:
			if s[left] != s[right]:
				return s[left:right] == s[left:right][::-1] or s[left + 1:right + 1] == s[left + 1:right + 1][::-1]
			else:
				left += 1
				right -= 1

		return True
```