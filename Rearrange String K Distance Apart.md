Given a string `s` and an integer `k`, rearrange `s` such that the same characters are **at least** distance `k` from each other. If it is not possible to rearrange the string, return an empty string `""`.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import Counter
import heapq

class Solution:
	def rearrangeString(self, s: str, k: int) -> str:
		char_counter, heap = Counter(s), []

		for c, count in char_counter.items():
			heapq.heappush(heap, (-count, c))

		cur_set, stack, result = set(), [], []
		while len(heap) > 0:
			neg_count, c = heapq.heappop(heap)
			if neg_count < -1:
				stack.append((neg_count + 1, c))

			if c in cur_set:
				return ""
			else:
				cur_set.add(c)

			result.append(c)

			if len(cur_set) >= k:
				for item in stack:
					heapq.heappush(heap, item)
				cur_set, stack = set(), []

		if len(s) == len("".join(result)):
			return "".join(result)
		else:
			return ""
```