Given two strings `s` and `t`, return `true` _if_ `t` _is an anagram of_ `s`_, and_ `false` _otherwise_.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process

# Solution
- asdada
```Python
from collections import defaultdict

class Solution:
	def isAnagram(self, s: str, t: str) -> bool:
		letters = defaultdict(int)

		for c in s:
			letters[c] += 1

		for c in t:
			letters[c] -= 1

		for c in letters:
			if letters[c] != 0:
				return False

		return True
```