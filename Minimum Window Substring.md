Given two strings `s` and `t` of lengths `m` and `n` respectively, return _the **minimum window substring_** _of_ `s` _such that every character in_ `t` _(**including duplicates**) is included in the window_. If there is no such substring, return _the empty string_ `""`.

The testcases will be generated such that the answer is **unique**.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
- 
# Solution
- asdasd
```Python
from collections import defaultdict

class Solution:
	def minWindow(self, s: str, t: str) -> str:
		cur_chars, t_chars = defaultdict(int), defaultdict(int)
		t_matches, matches = 0, 0
		left, right = 0, 0
		min_substring = ""

		for c in t:
			t_chars[c] += 1
		t_matches = len(t_chars)

		while right < len(s):
			cur_chars[s[right]] += 1

			if cur_chars[s[right]] == t_chars[s[right]]:
				matches += 1

				while matches == t_matches:
					if cur_chars[s[left]] == t_chars[s[left]]:
						matches -= 1

					if len(min_substring) == 0 or right - left + 1 < len(min_substring):
						min_substring = s[left:right + 1]
					cur_chars[s[left]] -= 1
					left += 1

			right += 1

		return min_substring
```