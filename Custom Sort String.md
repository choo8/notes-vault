You are given two strings order and s. All the characters of order are unique and were sorted in some custom order previously.

Permute the characters of s so that they match the order that order was sorted. More specifically, if a character x occurs before a character y in order, then x should occur before y in the permuted string.

Return any permutation of s that satisfies this property.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def customSortString(self, order: str, s: str) -> str:
		char_dict, idx = {}, 0
		for c in order:
			if c not in char_dict:
				char_dict[c] = idx
				idx += 1

		for c in s:
			if c not in char_dict:
				char_dict[c] = idx
				idx += 1

		return "".join(sorted(s, key=lambda c: char_dict[c]))
```