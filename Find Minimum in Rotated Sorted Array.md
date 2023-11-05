Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

- `[4,5,6,7,0,1,2]` if it was rotated `4` times.
- `[0,1,2,4,5,6,7]` if it was rotated `7` times.

Notice that **rotating** an array `[a[0], a[1], a[2], ..., a[n-1]]` 1 time results in the array `[a[n-1], a[0], a[1], a[2], ..., a[n-2]]`.

Given the sorted rotated array `nums` of **unique** elements, return _the minimum element of this array_.

You must write an algorithm that runs in `O(log n) time.`
# Solution Complexity
- $O(log n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def findMin(self, nums: List[int]) -> int:
		left, right = 0, len(nums) - 1

		while True:
			mid = left + (right - left) // 2

			if nums[left] < nums[right] or left == right:
				return nums[left]
			elif nums[mid] < nums[right]:
				if mid - 1 >= 0 and nums[mid - 1] < nums[mid]:
					right = mid - 1
				else:
					return nums[mid]
			else:
				if mid + 1 < len(nums) and nums[mid] < nums[mid + 1]:
					left = mid + 1
				else:
					return nums[mid + 1]
```