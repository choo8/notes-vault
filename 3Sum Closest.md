Given an integer array nums of length n and an integer target, find three integers in nums such that the sum is closest to target.

Return the sum of the three integers.

You may assume that each input would have exactly one solution.
# Solution Complexity
- $O(n^2)$ time complexity
- $O(n)$ space complexity
# Thought Process
- For bruteforce solution, we can iterate over 3 nested for loops to check all possible combinations of triples in `nums` against the `target` and track the triple that has a sum closest to `target`, in $O(n^3)$ time complexity and $O(1)$ space complexity
- To improve on the bruteforce solution, we need to reduce the search space and not enumerate all possible triples. First, we can sort `nums` so that we can eliminate certain elements by checking the distance of the triple's sum to `target`. Next, we can also employ the 2 pointer technique to reduce 
# Solution
- asdsad
```Python
import sys

class Solution:
	def threeSumClosest(self, nums: List[int], target: int) -> int:
		nums.sort()
		closest_sum, closest_dist = sys.maxsize, sys.maxsize

		for idx in range(len(nums) - 1):
			left, right = idx + 1, len(nums) - 1

			while left < right:
				cur_sum = nums[idx] + nums[left] + nums[right]
				if abs(cur_sum - target) < closest_dist:
					closest_dist = abs(cur_sum - target)
					closest_sum = cur_sum

				if cur_sum == target:
					return closest_sum
				elif cur_sum < target:
					left += 1
				else:
					right -= 1

		return closest_sum
```