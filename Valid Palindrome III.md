Given a string `s` and an integer `k`, return `true` if `s` is a `k`**-palindrome**.

A string is `k`**-palindrome** if it can be transformed into a palindrome by removing at most `k` characters from it.
# Solution Complexity
- $O(n^2)$ time complexity
- $O(n^2)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def isValidPalindrome(self, s: str, k: int) -> bool:
		# dp[i][j] represents longest palindrome in s[i..j] 
		dp = [[0 for _ in range(len(s))] for _ in range(len(s))]

		# All s[i..i] have only 1 character and are palindromes
		for i in range(len(s)):
			dp[i][i] = 1

		for i in range(len(s) - 1, -1, -1):
			for j in range(i + 1, len(s)):
				# s[i..j] is a palindrome
				if s[i] == s[j]:
					dp[i][j] = dp[i + 1][j - 1] + 2
				else:
					# Either remove s[i] or s[j]
					if i + 1 < len(s):
						dp[i][j] = max(dp[i][j], dp[i + 1][j])
					if j - 1 >= 0:
						dp[i][j] = max(dp[i][j], dp[i][j - 1])

		return dp[0][len(s) - 1] >= len(s) - k
```