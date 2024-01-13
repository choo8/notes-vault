Given an array of **distinct** integers `candidates` and a target integer `target`, return _a list of all **unique combinations** of_ `candidates` _where the chosen numbers sum to_ `target`_._ You may return the combinations in **any order**.

The **same** number may be chosen from `candidates` an **unlimited number of times**. Two combinations are unique if the frequency of at least one of the chosen numbers is different.

The test cases are generated such that the number of unique combinations that sum up to `target` is less than `150` combinations for the given input.
# Solution Complexity
- $O()$ time complexity
- $O()$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def combinationSum(self, candidates: List[int], target: int) -> List[List[int]]:
		self.sums = []

		self._helper(sorted(candidates), [], 0, target)

		return self.sums

	def _helper(self, candidates: List[int], cur_comb: List[int], cur_sum: int, target: int) -> None:
		if cur_sum == target:
			self.sums.append(cur_comb)
			return
		elif cur_sum > target:
			return

		for idx, c in enumerate(candidates):
			self._helper(candidates[idx:], cur_comb + [c], cur_sum + c, target)
```