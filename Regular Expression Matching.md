Given an input string `s` and a pattern `p`, implement regular expression matching with support for `'.'` and `'*'` where:

- `'.'` Matches any single character.​​​​
- `'*'` Matches zero or more of the preceding element.

The matching should cover the **entire** input string (not partial).
# Solution Complexity
- $O(nm)$ time complexity
- $O(nm)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def isMatch(self, s: str, p: str) -> bool:
		# Ensure that there are no 2 consecutive "*" characters in p
		normalized_p = []
		for idx, c in enumerate(p):
			if idx > 0 and c == "*" and p[idx - 1] == "*":
				continue
			normalized_p.append(c)
		normalized_p = "".join(normalized_p)

		dp = [[False for _ in range(len(normalized_p) + 1)] for _ in range(len(s) + 1)]
		dp[0][0] = True # Empty pattern matches empty string
		# Patterns with "*" can match empty strings
		for j, c_p in enumerate(normalized_p):
			shifted_j = j + 1
			if c_p == "*":
				dp[0][shifted_j] = dp[0][shifted_j - 2]

		for i, c_s in enumerate(s):
			for j, c_p in enumerate(normalized_p):
				# Shift indices due to sentinel value
				shifted_i, shifted_j = i + 1, j + 1
				# Exact match of character literal or pattern character is "."
				if c_s == c_p or c_p == ".":
					dp[shifted_i][shifted_j] = dp[shifted_i - 1][shifted_j - 1]
				elif c_p == "*":
					# "*" matches zero preceding element
					no_match = dp[shifted_i][shifted_j - 2]
					# "*" matches preceding element
					if normalized_p[j - 1] == c_s or normalized_p[j - 1] == ".":
						dp[shifted_i][shifted_j] = no_match or dp[shifted_i - 1][shifted_j]
					else:
						dp[shifted_i][shifted_j] = no_match

		return dp[-1][-1]
```