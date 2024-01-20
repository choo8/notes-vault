Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.

There is only **one repeated number** in `nums`, return _this repeated number_.

You must solve the problem **without** modifying the array `nums` and uses only constant extra space.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def findDuplicate(self, nums: List[int]) -> int:
		idx = 0

		while True:
			while nums[idx] != idx + 1:
				if nums[nums[idx] - 1] == nums[idx]:
					return nums[idx]
				temp = nums[nums[idx] - 1]
				nums[nums[idx] - 1] = nums[idx]
				nums[idx] = temp
			idx += 1
```