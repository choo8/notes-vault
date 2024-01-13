Given an array nums containing n distinct numbers in the range [0, n], return the only number in the range that is missing from the array.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def missingNumber(self, nums: List[int]) -> int:
		ret = 0

		for idx, n in enumerate(nums):
			ret = ret ^ (idx + 1) ^ n

		return ret
```