Given a list of non-negative integers `nums`, arrange them such that they form the largest number and return it.

Since the result may be very large, so you need to return a string instead of an integer.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asad
```Python
class Solution:
	def largestNumber(self, nums: List[int]) -> str:
		idx, nums = 0, self._mergeSort(nums)

		while idx < len(nums) - 1 and nums[idx] == 0:
			idx += 1
		
		return "".join([str(n) for n in nums[idx:]])

	def _mergeSort(self, nums: List[int]) -> List[int]:
		if len(nums) <= 1:
			return nums
		else:
			left, right = 0, len(nums) - 1
			mid = left + (right - left) // 2
	
			ret, l1, l2, idx1, idx2 = [], self._mergeSort(nums[:mid + 1]), self._mergeSort(nums[mid + 1:]), 0, 0

			while idx1 < len(l1) and idx2 < len(l2):
				if int(str(l1[idx1]) + str(l2[idx2])) >= int(str(l2[idx2]) + str(l1[idx1])):
					ret.append(l1[idx1])
					idx1 += 1
				else:
					ret.append(l2[idx2])
					idx2 += 1

			if idx1 != len(l1):
				ret += l1[idx1:]
			elif idx2 != len(l2):
				ret += l2[idx2:]

			return ret
```