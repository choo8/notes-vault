Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.
# Solution Complexity
$O(log(min(m,n)))$ time complexity
$O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
		if len(nums1) > len(nums2):
			nums1, nums2 = nums2, nums1

		len1, len2 = len(nums1), len(nums2)
		left1, right1, left2, right2 = 0, len1, 0, len2

		while True:
			mid1 = (left1 + right1) // 2
			mid2 = (len1 + len2 + 1) // 2 - mid1

			max1 = nums1[mid1 - 1] if mid1 > 0 else float("-inf")
			max2 = nums2[mid2 - 1] if mid2 > 0 else float("-inf")

			min1 = nums1[mid1] if mid1 < len1 else float('inf')
			min2 = nums2[mid2] if mid2 < len2 else float('inf')

			max_comb = max(max1, max2)
			min_comb = min(min1, min2)

			if max_comb <= min_comb:
				if (len1 + len2) % 2 == 0:
					return (max_comb + min_comb) / 2.0
				else:
					return max_comb
			elif max1 > min2:
				right1 = mid1 - 1
			else:
				left1 = mid1 + 1
```