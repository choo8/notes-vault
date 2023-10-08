Given an integer array `nums`, find a subarray that has the largest product, and return _the product_.

The test cases are generated so that the answer will fit in a **32-bit** integer.
# Solution Complexity
# Thought Process
# Solution
- safsdf
```Python
class Solution:
	def maxProductHelper(self, nums: List[int]) -> int:
		res = -float('inf')
		cur_neg, cur_pos = 0, 0

		for num in nums:
			if num > 0:
				cur_neg = cur_neg * num
				cur_pos = num if cur_pos == 0 else cur_pos * num
			elif num < 0:
				prev_neg, prev_pos = cur_neg, cur_pos
				cur_pos = cur_neg * num if cur_neg < 0 else 0
				cur_neg = 0 if cur_neg < 0 else max(prev_pos, 1) * num
			else:
				cur_neg, cur_pos = 0, 0
			res = max(res, cur_pos) if cur_pos > 0 else max(res, cur_neg)

		return res

	def maxProduct(self, nums: List[int]) -> int:	
		return max(self.maxProductHelper(nums), self.maxProductHelper(list(reversed(nums))))
```