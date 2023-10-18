 Given a string `s`, find the length of the **longest** **substring** without repeating characters.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
- The brute force solution is to iterate all possible substrings `s[i..j]` via a nested for loops and using another for loop, check if there are any repeating characters for each of the substring. Amongst those without any repeating characters, return the length of the longest one. This should result in a $O(n^3)$ time complexity algorithm while requiring a $O(1)$ space complexity.
- To improve on the naïve solution, we could make use of a sliding window to iterate through all possible substrings, resulting in an $O(n)$ time complexity algorithm to cover all possible substrings instead. While iterating through the substrings, we track the characters of the substring via a hash table. At the same time, we update the `max_len` variable as we iterate through the substrings.
# Solution
- Iterate through all possible substrings via a sliding window algorithm, moving the right pointer while keeping track of the number of characters in the substring via a hash table and the `max_len` variable as the right pointer moves right. Once a repeat character is detected, shrink the current substring until the repeated character is left out and continue progressing the right pointer. When the right pointer reaches the last character, we return `max_len`.
```Python
from collections import defaultdict

class Solution:
	def lengthOfLongestSubstring(self, s: str) -> int:
		chars = defaultdict(int)
		max_len = 0
		left, right = 0, 0

		while right < len(s):
			if chars[s[right]] == 1:
				while s[left] != s[right]:
					chars[s[left]] -= 1
					left += 1
				left += 1
				right += 1
			else:
				chars[s[right]] += 1
				max_len = max(max_len, right - left + 1)
				right += 1

		return max_len
```