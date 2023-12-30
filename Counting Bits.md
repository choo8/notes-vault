Given an integer `n`, return _an array_ `ans` _of length_ `n + 1` _such that for each_ `i` (`0 <= i <= n`)_,_ `ans[i]` _is the **number of**_ `1`_**'s** in the binary representation of_ `i`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adasd
```Python
class Solution:
	def countBits(self, n: int) -> List[int]:
		dp = [0] * (n + 1)

		for i in range(1, n + 1):
			if i & 1 == 1:
				dp[i] = dp[(i - 1) // 2] + 1
			else:
				dp[i] = dp[i // 2]

		return dp
```