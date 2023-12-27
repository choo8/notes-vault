Given an integer array `nums` and an integer `k`, return _the_ `k` _most frequent elements_. You may return the answer in **any order**.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adsad
```Python
from collections import defaultdict

class Solution:
	def topKFrequent(self, nums: List[int], k: int) -> List[int]:
		freq, num_to_freq = [set() for _ in range(len(nums) + 1)], defaultdict(int)
		res = []

		for n in nums:
			num_to_freq[n] += 1

			freq[num_to_freq[n]].add(n)
			if num_to_freq[n] > 1:
				freq[num_to_freq[n] - 1].remove(n)

		for idx in range(len(nums), -1 , -1):
			if len(freq[idx]) != 0:
				res += [n for n in freq[idx]]

				k -= len(freq[idx])

			if k == 0:
				break

		return res
```