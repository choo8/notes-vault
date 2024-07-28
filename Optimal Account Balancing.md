You are given an array of transactions `transactions` where `transactions[i] = [from_i, to_i, amount_i]` indicates that the person with `ID = from_i` gave `amount_i $` to the person with `ID = to_i`.

Return _the minimum number of transactions required to settle the debt_.
# Solution Complexity
- $O(n2^n)$ time complexity
- $O(2^n)$ space complexity
# Thought Process
# Solution
- asdasdas
```Python
from collections import defaultdict

class Solution:
	def minTransfers(self, transactions: List[List[int]]) -> int:
		balance = defaultdict(int)

		for i, j, amount in transactions:
			balance[i] -= amount
			balance[j] += amount

		balance = [amount for amount in balance.values() if amount != 0]

		dp = [inf for _ in range(1 << len(balance))]
		dp[0] = 0

		for i in range(1, 1 << len(balance)):
			total_debts = 0

			# Debt for current subset
			for j, debt in enumerate(balance):
				if i >> j & 1:
					total_debts += debt

			if total_debts == 0:
				dp[i] = bin(i).count("1") - 1

				# Remove right most "1"
				subset = (i - 1) & i
				while subset > 0:
					dp[i] = min(dp[i], dp[subset] + dp[i ^ subset])
					subset = (subset - 1) & i

		return dp[-1]
```