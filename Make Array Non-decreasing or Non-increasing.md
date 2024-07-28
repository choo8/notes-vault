You are given a **0-indexed** integer array `nums`. In one operation, you can:

- Choose an index `i` in the range `0 <= i < nums.length`
- Set `nums[i]` to `nums[i] + 1` **or** `nums[i] - 1`

Return _the **minimum** number of operations to make_ `nums` _**non-decreasing** or **non-increasing**._
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
import heapq

class Solution:
	def convertArray(self, nums: List[int]) -> int:
		# Decreasing
		heap, cur_ops = [], 0
		for n in nums:
			if len(heap) != 0 and heap[0] < n:
				cur_ops += n - heapq.heappop(heap)
				heapq.heappush(heap, n)
			heapq.heappush(heap, n)

		num_ops = cur_ops

		# Increasing
		heap, cur_ops = [], 0
		for n in nums:
			if len(heap) != 0 and heap[0] < -n:
				cur_ops += -n - heapq.heappop(heap)
				heapq.heappush(heap, -n)
			heapq.heappush(heap, -n)

		return min(num_ops, cur_ops)
```