Given an array `nums` with `n` objects colored red, white, or blue, sort them **[in-place](https://en.wikipedia.org/wiki/In-place_algorithm)** so that objects of the same color are adjacent, with the colors in the order red, white, and blue.

We will use the integers `0`, `1`, and `2` to represent the color red, white, and blue, respectively.

You must solve this problem without using the library's sort function.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def sortColors(self, nums: List[int]) -> None:
		"""
		Do not return anything, modify nums in-place instead.
		"""

		p_0 = 0
		while p_0 < len(nums) and nums[p_0] == 0:
			p_0 += 1

		p_1 = p_0
		while p_1 < len(nums) and nums[p_1] == 1:
			p_1 += 1

		p_2 = len(nums) - 1
		while p_2 >= 0 and nums[p_2] == 2:
			p_2 -= 1

		if p_0 == len(nums) or p_1 == len(nums) or p_2 < 0:
			return

		while p_1 <= p_2:
			if nums[p_1] == 0:
				nums[p_1] = nums[p_0]
				nums[p_0] = 0
				p_0 += 1
				p_1 = max(p_0, p_1)
			elif nums[p_1] == 2:
				nums[p_1] = nums[p_2]
				nums[p_2] = 2
				p_2 -= 1
			else:
				p_1 += 1
```