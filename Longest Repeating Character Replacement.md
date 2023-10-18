You are given a string `s` and an integer `k`. You can choose any character of the string and change it to any other uppercase English character. You can perform this operation at most `k` times.

Return _the length of the longest substring containing the same letter you can get after performing the above operations_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
- sdfasf
- fsadfsaf
# Solution
- aasdasd
```Python
from collections import defaultdict

class Solution:
	def characterReplacement(self, s: str, k: int) -> int:
		chars = defaultdict(int)
		left, right = 0, 0
		max_num_chars = 0
		max_len = 0

		while right < len(s):
			chars[s[right]] += 1
			max_num_chars = max(max_num_chars, chars[s[right]])
			
			while (right - left + 1) - max_num_chars > k:
				chars[s[left]] -= 1
				left += 1
			
			max_len = max(max_len, right - left + 1)
			right += 1

		return max_len
```