Given an array of **distinct** integers `nums` and a target integer `target`, return _the number of possible combinations that add up to_ `target`.

The test cases are generated so that the answer can fit in a **32-bit** integer.
# Solution Complexity
- $O(nk)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def combinationSum4(self, nums: List[int], target: int) -> int:
		dp = [0] * (target + 1)
		dp[0] = 1

		for idx in range(1, target + 1):
			for n in nums:
				if idx - n >= 0:
					dp[idx] += dp[idx - n]

		return dp[target]
```