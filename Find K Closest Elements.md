Given a **sorted** integer array `arr`, two integers `k` and `x`, return the `k` closest integers to `x` in the array. The result should also be sorted in ascending order.

An integer `a` is closer to `x` than an integer `b` if:

- `|a - x| < |b - x|`, or
- `|a - x| == |b - x|` and `a < b`
# Solution Complexity
- $O(logn + k)$ time complexity
- $O(k)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def findClosestElements(self, arr: List[int], k: int, x: int) -> List[int]:
		left, right = 0, len(arr) - 1

		while right - left > 1:
			mid = left + (right - left) // 2

			if arr[mid] <= x:
				left = mid
			else:
				right = mid

		smaller = left if abs(arr[left] - x) <= abs(arr[right] - x) else right
		left, right = smaller, smaller

		while right - left + 1 != k:
			if left == 0:
				right += k - (right - left + 1)
			elif right == len(arr) - 1:
				left -= k - (right - left + 1)
			else:
				if abs(arr[left - 1] - x) <= abs(arr[right + 1] - x):
					left -= 1
				else:
					right += 1

		return arr[left:right + 1]
```