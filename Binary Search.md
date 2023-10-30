Given an array of integers `nums` which is sorted in ascending order, and an integer `target`, write a function to search `target` in `nums`. If `target` exists, then return its index. Otherwise, return `-1`.

You must write an algorithm with `O(log n)` runtime complexity.
# Solution Complexity
- $O(log n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- adad
```Python
class Solution:
	def search(self, nums: List[int], target: int) -> int:
		return self._search(0, len(nums) - 1, nums, target)

	def _search(self, left: int, right: int, nums: List[int], target: int) -> int:
		if right < left:
			return -1

		mid = left + ((right - left) // 2)
		
		if nums[mid] == target:
			return mid
		elif nums[mid] > target:
			return self._search(left, right - 1, nums, target)
		else:
			return self._search(left + 1, right, nums, target)
```