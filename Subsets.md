Given an integer array `nums` of **unique** elements, return _all possible subsets (the power set)_.

The solution set **must not** contain duplicate subsets. Return the solution in **any order**.
# Solution Complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def subsets(self, nums: List[int]) -> List[List[int]]:
		self.nums = nums
		self.res = []

		self._combination(0, [])

		return self.res

	def _combination(self, idx: int, cur: List[int]) -> None:
		if idx == len(self.nums):
			self.res.append(cur)
			return

		self._combination(idx + 1, cur)
		self._combination(idx + 1, cur + [self.nums[idx]])
```