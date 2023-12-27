You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return _the maximum amount of money you can rob tonight **without alerting the police**_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdfsdf
```Python
class Solution:
	def rob(self, nums: List[int]) -> int:
		dp = [0] * len(nums)

		for idx in range(len(nums)):
			if idx == 0:
				dp[idx] = nums[idx]
			elif idx == 1:
				dp[idx] = max(nums[idx], nums[idx - 1])
			else:
				dp[idx] = max(nums[idx] + dp[idx - 2], dp[idx - 1])

		return dp[-1]
```