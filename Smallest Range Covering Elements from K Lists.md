You have `k` lists of sorted integers in **non-decreasing order**. Find the **smallest** range that includes at least one number from each of the `k` lists.

We define the range `[a, b]` is smaller than range `[c, d]` if `b - a < d - c` **or** `a < c` if `b - a == d - c`.
# Solution
- $O(nklogk)$ time complexity
- $O(k)$ space complexity
# Thought Process
# Solution
- asdas
```Python
import heapq
import sys

class Solution:
	def smallestRange(self, nums: List[List[int]]) -> List[int]:
		heap, range_max = [], -sys.maxsize
		for idx, l in enumerate(nums):
			heapq.heappush(heap, (l[0], 0, idx))
			range_max = max(range_max, l[0])
		range_min, smallest_range = heap[0][0], range_max - heap[0][0]

		cur_min, cur_max = range_min, range_max
		while True:
			cur_num, cur_idx, list_idx = heapq.heappop(heap)

			if cur_idx == len(nums[list_idx]):
				break

			next_num = nums[list_idx][cur_idx]
			cur_max = max(cur_max, next_num)
			heapq.heappush(heap, (next_num, cur_idx + 1, list_idx))

			if cur_max - heap[0][0] < smallest_range:
				range_min, range_max, smallest_range = heap[0][0], cur_max, cur_max - heap[0][0]

		return [range_min, range_max]
```