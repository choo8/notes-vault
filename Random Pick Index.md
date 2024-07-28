Given an integer array `nums` with possible **duplicates**, randomly output the index of a given `target` number. You can assume that the given target number must exist in the array.

Implement the `Solution` class:

- `Solution(int[] nums)` Initializes the object with the array `nums`.
- `int pick(int target)` Picks a random index `i` from `nums` where `nums[i] == target`. If there are multiple valid i's, then each index should have an equal probability of returning.
# Solution Complexity
- $O(n)$ time complexity for `__init__` operation and $O(1)$ time complexity for `pick` operation
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict
from random import sample

class Solution:
	def __init__(self, nums: List[int]):
		self.idx_dict = defaultdict(list)
		for idx, n in enumerate(nums):
			self.idx_dict[n].append(idx)

	def pick(self, target: int) -> int:
		return sample(self.idx_dict[target], 1)[0]

# Your Solution object will be instantiated and called as such:
# obj = Solution(nums)
# param_1 = obj.pick(target)
```