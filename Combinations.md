Given two integers `n` and `k`, return _all possible combinations of_ `k` _numbers chosen from the range_ `[1, n]`.

You may return the answer in **any order**.
# Solution Complexity
- $O(\binom{n}{k})$ time complexity
- $O(\binom{n}{k})$ space complexity
# Thought Process
# Solution
- adasd
```Python
class Solution:
	def combine(self, n: int, k: int) -> List[List[int]]:
		self.n = n
		self.k = k
		self.res = []
		self._combine(1, [])
		return self.res

	def _combine(self, cur: int, cur_comb: List[int]) -> None:
		if len(cur_comb) == self.k:
			self.res.append(cur_comb)
			return

		for idx, n in enumerate(range(cur, self.n + 1)):
			self._combine(n + 1, cur_comb + [n])
```