Given an integer array `nums` sorted in **non-decreasing order**, remove some duplicates [**in-place**](https://en.wikipedia.org/wiki/In-place_algorithm) such that each unique element appears **at most twice**. The **relative order** of the elements should be kept the **same**.

Since it is impossible to change the length of the array in some languages, you must instead have the result be placed in the **first part** of the array `nums`. More formally, if there are `k` elements after removing the duplicates, then the first `k` elements of `nums` should hold the final result. It does not matter what you leave beyond the first `k` elements.

Return `k` _after placing the final result in the first_ `k` _slots of_ `nums`.

Do **not** allocate extra space for another array. You must do this by **modifying the input array [in-place](https://en.wikipedia.org/wiki/In-place_algorithm)** with O(1) extra memory.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def removeDuplicates(self, nums: List[int]) -> int:
		if len(nums) == 0:
			return 0

		left, right = 0, 0
		while right < len(nums):
			# 2 or more of the same element
			if right + 1 < len(nums) and nums[right + 1] == nums[right]:
				nums[left], nums[left + 1] = nums[right], nums[right + 1]
				left += 2
				right += 2

				# ignore rest of duplicates
				while right < len(nums) and nums[right - 1] == nums[right]:
					right += 1
			# no duplicate elements
			else:
				nums[left] = nums[right]
				left += 1
				right += 1

		return left
```