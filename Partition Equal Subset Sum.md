Given an integer array `nums`, return `true` _if you can partition the array into two subsets such that the sum of the elements in both subsets is equal or_ `false` _otherwise_.
# Solution Complexity
- $O(nk)$ time complexity
- $O(k)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def canPartition(self, nums: List[int]) -> bool:
		total = sum(nums)

		if total % 2 == 1:
			return False

		dp = [False for _ in range((total // 2) + 1)]
		dp[0] = True

		for n in nums:
			for j in range((total // 2) - n, -1, -1):
				dp[j + n] |= dp[j]

		return dp[total // 2]
```