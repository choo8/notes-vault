Given an unsorted integer array `nums`, return the smallest missing positive integer.

You must implement an algorithm that runs in `O(n)` time and uses `O(1)` auxiliary space.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
- Since we are limited by $O(1)$ space complexity, we cannot simply record down everything we see in the `nums` array, but instead, can only used a fixed number of helper variables, or some sort of statistic during the computation. Also, with the $O(n)$ time complexity requirement, we cannot sort the array (needs $O(nlogn)$), and will need to perform some kind of $O(1)$ computation per element, or run through the array a fixed amount of times
- If we did not have the space requirement, we could hash every number in `nums` into a hash table, and iterate from 1 to `len(nums)` to check for the first missing positive number
- The key insight is that while we cannot incur an additional $O(n)$ space complexity with the hash table, we are only interested in positive keys that start from 1 and end at `len(nums)`, since the largest possible first missing positive must be `len(nums) + 1`, in the case where 1 to `len(nums)` are all in the array. Hence, we can repurpose the `nums` array to be a hash table, using its position as an index, and hashing the elements by swapping them in-place (i.e. `n` goes to index `n - 1` of `nums`)
# Solution
- adasdasd
```Python
class Solution:
	def firstMissingPositive(self, nums: List[int]) -> int:
		temp = -1
		nums_len = len(nums)
		
		for idx, n in enumerate(nums):
			temp = n
			while temp > 0 and temp <= nums_len:
				_temp = nums[temp - 1]
				nums[temp - 1] = temp
				if temp != _temp:
					temp = _temp
				else:
					break

		for idx, n in enumerate(nums):
			if idx != n:
				return idx + 1
```