Given an integer array `nums` sorted in **non-decreasing** order, return _an array of **the squares of each number** sorted in non-decreasing order_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def sortedSquares(self, nums: List[int]) -> List[int]:
		cur, left, right = len(nums) - 1, 0, len(nums) - 1
		ret = [0] * len(nums)

		while cur >= 0:
			if nums[left] ** 2 > nums[right] ** 2:
				ret[cur] = nums[left] ** 2
				left += 1
			else:
				ret[cur] = nums[right] ** 2
				right -= 1
			cur -= 1

		return ret
```