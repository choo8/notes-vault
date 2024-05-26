There is an integer array `nums` sorted in non-decreasing order (not necessarily with **distinct** values).

Before being passed to your function, `nums` is **rotated** at an unknown pivot index `k` (`0 <= k < nums.length`) such that the resulting array is `[nums[k], nums[k+1], ..., nums[n-1], nums[0], nums[1], ..., nums[k-1]]` (**0-indexed**). For example, `[0,1,2,4,4,4,5,6,6,7]` might be rotated at pivot index `5` and become `[4,5,6,6,7,0,1,2,4,4]`.

Given the array `nums` **after** the rotation and an integer `target`, return `true` _if_ `target` _is in_ `nums`_, or_ `false` _if it is not in_ `nums`_._

You must decrease the overall operation steps as much as possible.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def search(self, nums: List[int], target: int) -> bool:
		left, right = 0, len(nums) - 1

		while left <= right:
			mid = left + (right - left) // 2

			if target == nums[mid] or target == nums[left] or target == nums[right]:
				return True
			elif nums[mid] < nums[right]:
				if nums[mid] < target and target < nums[right]:
					left = mid + 1
				else:
					right = mid - 1
			elif nums[mid] > nums[right]:
				if nums[left] < target and target < nums[mid]:
					right = mid - 1
				else:
					left = mid + 1
			else:
				right -= 1

		return False
```