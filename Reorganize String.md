Given a string `s`, rearrange the characters of `s` so that any two adjacent characters are not the same.

Return _any possible rearrangement of_ `s` _or return_ `""` _if not possible_.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasdsad
```Python
from collections import Counter
import heapq

class Solution:
	def reorganizeString(self, s: str) -> str:
		new_s, heap = [], []

		for c, count in Counter(s).items():
			heapq.heappush(heap, (-count, c))

		prev = None
		while len(heap) > 0:
			neg_count, c = heapq.heappop(heap)

			if not prev or prev != c:
				new_s.append(c)
				prev = c

				if neg_count < -1:
					heapq.heappush(heap, (neg_count + 1, c))
			elif len(heap) != 0:
				neg_count_next, c_next = heapq.heappop(heap)

				new_s.append(c_next)
				prev = c_next

				if neg_count_next < -1:
					heapq.heappush(heap, (neg_count_next + 1, c_next))
				heapq.heappush(heap, (neg_count, c))
			else:	
				return ""

		return "".join(new_s)
```