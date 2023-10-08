Given an integer array `nums`, return `true` if any value appears **at least twice** in the array, and return `false` if every element is distinct.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
- 
# Solution
- sdfasdf
```Python
class Solution:
	def containsDuplicate(self, nums: List[int]) -> bool:
		cache = {}

		for num in nums:
			if num in cache:
				return True
			else:
				cache[num] = True

		return False
```