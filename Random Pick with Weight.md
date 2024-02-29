You are given a **0-indexed** array of positive integers `w` where `w[i]` describes the **weight** of the `ith` index.

You need to implement the function `pickIndex()`, which **randomly** picks an index in the range `[0, w.length - 1]` (**inclusive**) and returns it. The **probability** of picking an index `i` is `w[i] / sum(w)`.

- For example, if `w = [1, 3]`, the probability of picking index `0` is `1 / (1 + 3) = 0.25` (i.e., `25%`), and the probability of picking index `1` is `3 / (1 + 3) = 0.75` (i.e., `75%`).
# Solution Complexity
- $O(n)$ time complexity for `__init__` and $O(logn)$ time complexity for `pickIndex` operation
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
import random

class Solution:
	def __init__(self, w: List[int]):
		self.freq = [w[0] for _ in range(len(w))]

		for idx, n in enumerate(w[1:]):
			self.freq[idx + 1] = self.freq[idx] + n

	def pickIndex(self) -> int:
		rand_idx = random.randint(1, self.freq[-1])

		left, right = 0, len(self.freq) - 1

		while left < right:
			mid = left + (right - left) // 2

			if self.freq[mid] < rand_idx:
				left = mid + 1
			else:
				right = mid

		return left
# Your Solution object will be instantiated and called as such:
# obj = Solution(w)
# param_1 = obj.pickIndex()
```