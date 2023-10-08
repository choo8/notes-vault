There is an integer array `nums` sorted in ascending order (with **distinct** values).

Prior to being passed to your function, `nums` is **possibly rotated** at an unknown pivot index `k` (`1 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,5,6,7]` might be rotated at pivot index `3` and become `[4,5,6,7,0,1,2]`.

Given the array `nums` **after** the possible rotation and an integer `target`, return _the index of_ `target` _if it is in_ `nums`_, or_ `-1` _if it is not in_ `nums`.

You must write an algorithm with `O(log n)` runtime complexity.
# Solution Complexity
# Thought Process
# Solution
- dasd
```Python
class Solution:
	def _search(self, nums: List[int], left: int, right: int, target: int) -> int:
		if left > right:
			return -1
		
		middle = left + int((right - left) / 2)

		if target == nums[middle]:
			return middle
		elif target < nums[middle]:
			if nums[left] > nums[middle] or target >= nums[left]:
				return self._search(nums, left, middle - 1, target)
			else:
				return self._search(nums, middle + 1, right, target)
		else:
			if nums[right] < nums[middle] or target <= nums[right]:
				return self._search(nums, middle + 1, right, target)
			else:
				return self._search(nums, left, middle - 1, target)

	def search(self, nums: List[int], target: int) -> int:
		return self._search(nums, 0, len(nums) - 1, target)
```