Given an integer array `nums`, rotate the array to the right by `k` steps, where `k` is non-negative.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def rotate(self, nums: List[int], k: int) -> None:
		"""
		Do not return anything, modify nums in-place instead.
		"""
		k = k % len(nums)

		self._reverse(0, len(nums) - 1, nums)
		self._reverse(0, k - 1, nums)
		self._reverse(k, len(nums) - 1, nums)

	def _reverse(self, start_idx: int, end_idx: int, nums:List[int]) -> None:
		while start_idx < end_idx:
			nums[start_idx], nums[end_idx] = nums[end_idx], nums[start_idx]
			start_idx += 1
			end_idx -= 1
```