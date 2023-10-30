Given an integer array `nums` that may contain duplicates, return _all possible subsets (the power set)_.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.
# Solution Complexity
# Thought Process
# Solution
- asdasdasd
```Python
class Solution:
	def subsetsWithDup(self, nums: List[int]) -> List[List[int]]:
		self.nums = sorted(nums)
		self.res = []

		self._combinations(0, [])

		return self.res

	def _combinations(self, idx: int, cur: List[int]) -> None:
		if idx == len(self.nums):
			self.res.append(cur)
			return

		self._combinations(idx + 1, cur + [self.nums[idx]])

		while idx + 1 < len(self.nums) and self.nums[idx] == self.nums[idx + 1]:
			idx += 1

		self._combinations(idx + 1, cur)
```