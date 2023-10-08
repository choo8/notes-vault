Given an integer array `nums`, find the subarray with the largest sum, and return _its sum_.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
- The bruteforce solution would be to iterate all subarrays `nums[i..j]`, where `i < j`, and calculate each of their sums, resulting in a $O(n^3)$ time complexity algorithm, while having a $O(1)$ space complexity.
- To improve on the naïve solution, we can reduce the time complexity to $O(n^2)$ by making use of prefix and suffix sums, while having a $O(n)$ space complexity.
- 
# Solution
- sfsdf
```Python
class Solution:
	def maxSubArray(self, nums: List[int]) -> int:
		cur, res = 0, -float('inf')

		for num in nums:
			cur = max(num, num + cur)
			res = max(res, cur)

		return res
```