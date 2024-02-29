Given two integers `dividend` and `divisor`, divide two integers **without** using multiplication, division, and mod operator.

The integer division should truncate toward zero, which means losing its fractional part. For example, `8.345` would be truncated to `8`, and `-2.7335` would be truncated to `-2`.

Return _the **quotient** after dividing_ `dividend` _by_ `divisor`.

**Note:** Assume we are dealing with an environment that could only store integers within the **32-bit** signed integer range: `[−231, 231 − 1]`. For this problem, if the quotient is **strictly greater than** `231 - 1`, then return `231 - 1`, and if the quotient is **strictly less than** `-231`, then return `-231`.
# Solution Complexity
- $O(logn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def divide(self, dividend: int, divisor: int) -> int:
		if divisor == -1:
			return (2 ** 31) - 1 if dividend == -2 ** 31 else -dividend
		elif divisor == -2 ** 31:
			return 1 if dividend == -2 ** 31 else 0
		elif abs(dividend) < abs(divisor):
			return 0

		is_positive = (dividend > 0) == (divisor > 0)
		divisor, quotient = abs(divisor), 0

		# Make dividend positive after substracting divisor once, while avoiding overflow
		dividend = dividend - divisor if dividend > 0 else -(dividend + divisor)

		cur_quotient, cur_divisor = 1, divisor
		while cur_divisor < 2 ** 30 and  cur_divisor << 1 <= dividend:
			cur_quotient, cur_divisor = cur_quotient << 1, cur_divisor << 1

		quotient = 1
		while divisor <= dividend:
			while cur_divisor > dividend:
				cur_divisor, cur_quotient = cur_divisor >> 1, cur_quotient >> 1
			dividend -= cur_divisor
			quotient += cur_quotient

		return quotient if is_positive else -quotient
```