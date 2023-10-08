Given an integer array nums, return all the triplets `[nums[i], nums[j], nums[k]]` such that `i != j`, `i != k`, and `j != k`, and `nums[i] + nums[j] + nums[k] == 0`.

Notice that the solution set must not contain duplicate triplets.
# Time Complexity
# Thought Process
# Solution
- asdfsdaf
```Python
class Solution:
	def threeSum(self, nums: List[int]) -> List[List[int]]:
		sorted_nums = sorted(nums)
		cache = {}
		res = []

		for i, num in enumerate(sorted_nums):
			cache[0 - num] = i

		i = 0
		while i < len(sorted_nums):
			j = i + 1
			while j < len(sorted_nums):
				if sorted_nums[i] + sorted_nums[j] in cache and i < cache[sorted_nums[i] + sorted_nums[j]] and j < cache[sorted_nums[i] + sorted_nums[j]]:
					res.append([sorted_nums[i], sorted_nums[j], 0 - sorted_nums[i] - sorted_nums[j]])
				j += 1
				while j < len(sorted_nums) and sorted_nums[j] == sorted_nums[j - 1]:
					j += 1
			i += 1
			while i < len(sorted_nums) and sorted_nums[i] == sorted_nums[i - 1]:
				i += 1

		return res
```