You are given an integer array `coins` representing coins of different denominations and an integer `amount` representing a total amount of money.

Return _the fewest number of coins that you need to make up that amount_. If that amount of money cannot be made up by any combination of the coins, return `-1`.

You may assume that you have an infinite number of each kind of coin.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def coinChange(self, coins: List[int], amount: int) -> int:
		dp = [-1] * (amount + 1)
		dp[0] = 0

		for a in range(amount + 1):
			for c in coins:
				if a == c:
					dp[a] = 1
				elif a - c >= 0 and dp[a - c] != -1:
					dp[a] = dp[a - c] + 1 if dp[a] == -1 else min(dp[a], dp[a - c] + 1)

		return dp[amount]
```