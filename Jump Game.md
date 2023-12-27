You are given an integer array `nums`. You are initially positioned at the array's **first index**, and each element in the array represents your maximum jump length at that position.

Return `true` _if you can reach the last index, or_ `false` _otherwise_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def canJump(self, nums: List[int]) -> bool:
		cur_furthest = 0

		for idx in range(len(nums)):
			if idx <= cur_furthest:
				cur_furthest = max(cur_furthest, idx + nums[idx])

		return cur_furthest >= len(nums) - 1
```