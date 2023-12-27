You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed. All houses at this place are **arranged in a circle.** That means the first house is the neighbor of the last one. Meanwhile, adjacent houses have a security system connected, and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Given an integer array `nums` representing the amount of money of each house, return _the maximum amount of money you can rob tonight **without alerting the police**_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- ads
```Python
class Solution:
	def rob(self, nums: List[int]) -> int:
		if len(nums) == 1:
			return nums[0]
		elif len(nums) == 2:
			return max(nums)

		with_first = [0] * (len(nums) - 1)
		with_last = [0] * (len(nums) - 1)

		for idx in range(len(nums)):
			if idx == 0:
				with_first[idx] = nums[idx]
			elif idx == 1:
				with_first[idx] = max(nums[idx - 1], nums[idx])
				with_last[idx - 1] = nums[idx]
			else:
				if idx < len(nums) - 1:
					with_first[idx] = max(with_first[idx - 2] + nums[idx], with_first[idx - 1])
				with_last[idx - 1] = max(with_last[idx - 2 - 1] + nums[idx], with_last[idx - 1 - 1])

		return max(with_first[-1], with_last[-1])
```