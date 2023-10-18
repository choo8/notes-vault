Given two strings `s` and `p`, return _an array of all the start indices of_ `p`_'s anagrams in_ `s`. You may return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict

class Solution:
	def findAnagrams(self, s: str, p: str) -> List[int]:
		cur_chars, p_chars = defaultdict(int), defaultdict(int)
		left, right = 0, 0
		matches, p_matches = 0, 0
		res = []

		for c in p:
			p_chars[c] += 1
		p_matches = len(p_chars)

		while right < len(s):
			cur_chars[s[right]] += 1

			if cur_chars[s[right]] == p_chars[s[right]]:
				matches += 1

				if matches == p_matches:
					cur_chars[s[left]] -= 1
					left += 1
					res.append(right - len(p) + 1)
			elif cur_chars[s[right]] > p_chars[s[right]]:
				if p_chars[s[right]] == 0:
					cur_chars = defaultdict(int)
					left = right + 1
				else:
					while cur_chars[s[right]] > p_chars[s[right]]:
						if cur_chars[s[left]] == p_chars[s[left]]:
							matches -= 1
						cur_chars[s[left]] -= 1
						left += 1

			right += 1

		return res
```