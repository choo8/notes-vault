Write a function to find the longest common prefix string amongst an array of strings.

If there is no common prefix, return an empty string "".
# Solution Complexity
- $O(nk)$ time complexity
- $O(k)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def longestCommonPrefix(self, strs: List[str]) -> str:
		longest = strs[0]

		for s in strs[1:]:
			for idx, c in enumerate(longest):
				if idx >= len(s):
					longest = s
					break
				elif idx < len(s) and longest[idx] != s[idx]:
					longest = s[:idx]
					break

		return longest
```