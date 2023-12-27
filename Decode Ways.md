A message containing letters from `A-Z` can be **encoded** into numbers using the following mapping:

'A' -> "1"
'B' -> "2"
...
'Z' -> "26"

To **decode** an encoded message, all the digits must be grouped then mapped back into letters using the reverse of the mapping above (there may be multiple ways). For example, `"11106"` can be mapped into:

- `"AAJF"` with the grouping `(1 1 10 6)`
- `"KJF"` with the grouping `(11 10 6)`

Note that the grouping `(1 11 06)` is invalid because `"06"` cannot be mapped into `'F'` since `"6"` is different from `"06"`.

Given a string `s` containing only digits, return _the **number** of ways to **decode** it_.

The test cases are generated so that the answer fits in a **32-bit** integer.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def numDecodings(self, s: str) -> int:
		dp = [0] * len(s)

		for idx in range(len(s)):
			if idx == 0:
				dp[idx] = 1 if s[idx] >= "1" and s[idx] <= "9" else 0
			elif idx == 1:
				dp[idx] = 1 if s[idx - 1] != "0" and s[idx] >= "1" and s[idx] <= "9" else 0

				if s[:idx + 1] >= "10" and s[:idx + 1] <= "26":
					dp[idx] += 1
			else:
				if s[idx] >= "1" and s[idx] <= "9":
					dp[idx] += dp[idx - 1]
				if s[idx - 1:idx + 1] >= "10" and s[idx - 1:idx + 1] <= "26":
					dp[idx] += dp[idx - 2]

		return dp[-1]
```