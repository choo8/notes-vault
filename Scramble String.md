We can scramble a string s to get a string t using the following algorithm:

1. If the length of the string is 1, stop.
2. If the length of the string is > 1, do the following:
    - Split the string into two non-empty substrings at a random index, i.e., if the string is `s`, divide it to `x` and `y` where `s = x + y`.
    - **Randomly** decide to swap the two substrings or to keep them in the same order. i.e., after this step, `s` may become `s = x + y` or `s = y + x`.
    - Apply step 1 recursively on each of the two substrings `x` and `y`.

Given two strings `s1` and `s2` of **the same length**, return `true` if `s2` is a scrambled string of `s1`, otherwise, return `false`.
# Solution Complexity
- $O(n^4)$ time complexity
- $O(n^3)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def isScramble(self, s1: str, s2: str) -> bool:
		# dp[i][j][k] indicates s1[i:i+k] matches s2[j:j+k]
		dp = [[[False for _ in range(len(s1) + 1)] for _ in range(len(s1))] for _ in range(len(s1))]

		# Match single characters from s1 and s2
		for i in range(len(s1)):
			for j in range(len(s2)):
				if s1[i] == s2[j]:
					dp[i][j][1] = True

		# Iterate over all s1[i:i+l] and s2[j:j+l]
		for l in range(2, len(s1) + 1):
			for i in range(len(s1) - l + 1):
				for j in range(len(s2) - l + 1):
					# len(x) = 1 to l - 1
					for x in range(1, l):
						if (dp[i][j][x] and dp[i + x][j + x][l - x]) or (dp[i][j + l - x][x] and dp[i + x][j][l - x]):
							dp[i][j][l] = True

		return dp[0][0][len(s1)]
```