Given an integer array `nums`, return _the length of the longest **strictly increasing subsequence**_.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def lengthOfLIS(self, nums: List[int]) -> int:
		ans = [nums[0]]

		for idx in range(1, len(nums)):
			if nums[idx] > ans[-1]:
				ans.append(nums[idx])
			else:
				left, right = 0, len(ans) - 1

				while left < right:
					mid = left + (right - left) // 2

					if nums[idx] > ans[mid]:
						left = mid + 1
					else:
						right = mid

				ans[left] = nums[idx]

		return len(ans)
```