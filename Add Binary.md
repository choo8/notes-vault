Given two binary strings `a` and `b`, return _their sum as a binary string_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adasd
```Python
class Solution:
	def addBinary(self, a: str, b: str) -> str:
		ret, carry = [], 0

		if len(b) > len(a):
			a, b = b, a

		for idx in range(-1, -len(a) - 1, -1):
			if idx >= -len(b):
				ret.append(str(int(a[idx]) ^ int(b[idx]) ^ carry))
				carry = (int(a[idx]) & int(b[idx])) | (int(b[idx]) & carry) | (carry & int(a[idx]))
			else:
				ret.append(str(int(a[idx]) ^ carry))
				carry = carry & int(a[idx])

		if carry == 1:
			ret.append(str(carry))

		return "".join(ret[::-1])
```