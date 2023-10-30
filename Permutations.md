Given an array `nums` of distinct integers, return _all the possible permutations_. You can return the answer in **any order**.
# Solution Complexity
- $O()$ time complexity
# Thought Process
# Solution
- adasd
```Python
class Solution:
	def permute(self, nums: List[int]) -> List[List[int]]:
		self.res = []
		self.nums = nums
		self.nums_len = len(nums)

		self._permutations(self.nums, [])

		return self.res

	def _permutations(self, cur_nums: List[int], cur_perm: List[int]) -> None:
		if len(cur_perm) == self.nums_len:
			self.res.append(cur_perm)
			return

		for idx, _ in enumerate(cur_nums):
			tmp = cur_nums.pop(idx)
			self._permutations(cur_nums, cur_perm + [tmp])
			cur_nums.insert(idx, tmp)
```