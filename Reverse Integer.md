Given a signed 32-bit integer `x`, return `x` _with its digits reversed_. If reversing `x` causes the value to go outside the signed 32-bit integer range `[-231, 231 - 1]`, then return `0`.

**Assume the environment does not allow you to store 64-bit integers (signed or unsigned).**
# Solution Complexity
- $O(logn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def reverse(self, x: int) -> int:
		ret, is_neg = 0, x < 0
		x = abs(x)

		while x >= 10:
			if ret > (2 ** 31) // 10:
				return 0

			ret *= 10
			ret += x % 10
			x = x // 10

		if x > 0:
			if ret > (2 ** 31) // 10:
				return 0

			ret *= 10
			ret += x

		return ret if not is_neg else -ret
```