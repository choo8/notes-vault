Implement [pow(x, n)](http://www.cplusplus.com/reference/valarray/pow/), which calculates `x` raised to the power `n` (i.e., `xn`).
# Solution Complexity
- $O(logn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def myPow(self, x: float, n: int) -> float:
		if n == 0:
			return 1
		elif n < 0:
			return 1.0 / self.myPow(x, -n)
		else:
			if n % 2 == 1:
				return x * self.myPow(x, n - 1)
			else:
				return self.myPow(x * x, n / 2)
```