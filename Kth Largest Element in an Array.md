Given an integer array `nums` and an integer `k`, return _the_ `kth` _largest element in the array_.

Note that it is the `kth` largest element in the sorted order, not the `kth` distinct element.

Can you solve it without sorting?
# Solution Complexity
# Thought Process
# Solution
- asdad
```Python
from random import randint

class Solution:
	def findKthLargest(self, nums: List[int], k: int) -> int:
		left, right = 0, len(nums) - 1

		while True:
			pivotIdx = self._partition(left, right, nums)

			if pivotIdx == len(nums) - k:
				return nums[pivotIdx]
			elif pivotIdx < len(nums) - k:
				left = pivotIdx + 1
			else:
				right = pivotIdx - 1

	def _partition(self, left: int, right: int, nums: List[int]) -> int:
		pivotIdx = randint(left, right)

		nums[right], nums[pivotIdx] = nums[pivotIdx], nums[right]

		pivotIdx = right
		swap = left

		for idx in range(left, right):
			if nums[idx] <= nums[pivotIdx]:
				nums[idx], nums[swap] = nums[swap], nums[idx]
				swap += 1

		nums[swap], nums[pivotIdx] = nums[pivotIdx], nums[swap]

		return swap
```
- asdasd
```Python
import heapq

class Solution:
    def findKthLargest(self, nums: List[int], k: int) -> int:
        return heapq.nlargest(k, nums)[-1]
```