Given an unsorted array of integers `nums`, return _the length of the longest consecutive elements sequence._

You must write an algorithm that runs in `O(n)` time.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def longestConsecutive(self, nums: List[int]) -> int:
		ret, nums_set = 0, set(nums)

		for n in nums_set:
			if n - 1 not in nums_set:
				cur_n, cur_longest = n, 0

				while cur_n in nums_set:
					cur_n += 1
					cur_longest += 1

				ret = max(ret, cur_longest)

		return ret
```