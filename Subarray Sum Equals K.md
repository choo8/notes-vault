Given an array of integers `nums` and an integer `k`, return _the total number of subarrays whose sum equals to_ `k`.

A subarray is a contiguous **non-empty** sequence of elements within an array.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
from collections import defaultdict

class Solution:
	def subarraySum(self, nums: List[int], k: int) -> int:
		ret, prefix_sum, prefix_sum_dict = 0, [nums[0] for _ in range(len(nums))], defaultdict(int)

		for idx, n in enumerate(nums):
			if idx > 0:
				prefix_sum[idx] = prefix_sum[idx - 1] + n

			if prefix_sum[idx] == k:
				ret += 1
			if prefix_sum[idx] - k in prefix_sum_dict:
				ret += prefix_sum_dict[prefix_sum[idx] - k]

			prefix_sum_dict[prefix_sum[idx]] += 1

		return ret
```