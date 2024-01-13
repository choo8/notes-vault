Reverse bits of a given 32 bits unsigned integer.

**Note:**

- Note that in some languages, such as Java, there is no unsigned integer type. In this case, both input and output will be given as a signed integer type. They should not affect your implementation, as the integer's internal binary representation is the same, whether it is signed or unsigned.
- In Java, the compiler represents the signed integers using [2's complement notation](https://en.wikipedia.org/wiki/Two%27s_complement). Therefore, in **Example 2** above, the input represents the signed integer `-3` and the output represents the signed integer `-1073741825`.
# Solution Complexity
- $O(1)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- sadasd
```Python
class Solution:
	def reverseBits(self, n: int) -> int:
		ret = 0

		for i in range(32):
			ret = (ret << 1) | ((n >> i) & 1)

		return ret
```