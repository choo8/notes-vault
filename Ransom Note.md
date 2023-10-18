Given two strings `ransomNote` and `magazine`, return `true` _if_ `ransomNote` _can be constructed by using the letters from_ `magazine` _and_ `false` _otherwise_.

Each letter in `magazine` can only be used once in `ransomNote`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adasd
```Python
from collections import Counter

class Solution:
	def canConstruct(self, ransomNote: str, magazine: str) -> bool:
		magazine_counter = Counter(magazine)

		for c in ransomNote:
			if c not in magazine_counter or magazine_counter[c] == 0:
				return False
			else:
				magazine_counter[c] -= 1

		return True
```