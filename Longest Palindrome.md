Given a string `s` which consists of lowercase or uppercase letters, return _the length of the **longest palindrome**_ that can be built with those letters.

Letters are **case sensitive**, for example, `"Aa"` is not considered a palindrome here.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict

class Solution:
	def longestPalindrome(self, s: str) -> int:
		ret, char_dict = 0, defaultdict(int)

		for c in s:
			char_dict[c] += 1

			if char_dict[c] % 2 == 0:
				ret += 2

		return ret if len(s) == ret else ret + 1
```