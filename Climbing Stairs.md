You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdfasdf
```Python
class Solution:
	def climbStairs(self, n: int) -> int:
		dp = [1] * (n + 1)

		for idx in range(1, n + 1):
			if idx > 1:
				dp[idx] = dp[idx - 2] + dp[idx - 1]
			else:
				dp[idx] = dp[idx - 1]

		return dp[n]
```