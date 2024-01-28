Given a binary array `nums`, return _the maximum length of a contiguous subarray with an equal number of_ `0` _and_ `1`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def findMaxLength(self, nums: List[int]) -> int:
		ret, cur_sum, sum_dict = 0, 0, {}

		for idx, n in enumerate(nums):
			if n == 0:
				cur_sum -= 1
			else:
				cur_sum += 1

			if cur_sum not in sum_dict:
				sum_dict[cur_sum] = idx

			if cur_sum == 0:
				ret = max(ret, idx + 1)
			if cur_sum in sum_dict:
				ret = max(ret, idx - sum_dict[cur_sum])

		return ret
```