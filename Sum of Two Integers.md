Given two integers `a` and `b`, return _the sum of the two integers without using the operators_ `+` _and_ `-`.
# Solution Complexity
- $O(logn)$ time complexity
- $O(logn)$ space complexity
# Thought Process
# Solution
- sdafasdf
```Python
class Solution:
	def getSum(self, a: int, b: int) -> int:
		mask = 0xffffffff
		a &= mask

		while b != 0:
			carry = a & b 
			a = (a ^ b) & mask
			b = (carry << 1) & mask

		if (a >> 31) & 1 == 1:
			return ~(a ^ mask)

		return a
```