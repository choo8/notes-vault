Given two strings `text1` and `text2`, return _the length of their longest **common subsequence**._ If there is no **common subsequence**, return `0`.

A **subsequence** of a string is a new string generated from the original string with some characters (can be none) deleted without changing the relative order of the remaining characters.

- For example, `"ace"` is a subsequence of `"abcde"`.

A **common subsequence** of two strings is a subsequence that is common to both strings.
# Solution Complexity
- $O(nm)$ time complexity
- $O(nm)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def longestCommonSubsequence(self, text1: str, text2: str) -> int:
		if len(text2) > len(text1):
			text1, text2 = text2, text1

		dp = [[0 for _ in range(len(text2))] for _ in range(len(text1))]

		for i in range(len(text1)):
			for j in range(len(text2)):
				if text1[i] == text2[j]:
					dp[i][j] = dp[i - 1][j - 1] + 1 if i > 0 and j > 0 else 1
				else:
					dp[i][j] = max(dp[i - 1][j] if i > 0 else 0, dp[i][j - 1] if j > 0 else 0)

		return dp[-1][-1]
```