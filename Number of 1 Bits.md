Write a function that takes the binary representation of an unsigned integer and returns the number of '1' bits it has (also known as the [Hamming weight](http://en.wikipedia.org/wiki/Hamming_weight)).

**Note:**

- Note that in some languages, such as Java, there is no unsigned integer type. In this case, the input will be given as a signed integer type. It should not affect your implementation, as the integer's internal binary representation is the same, whether it is signed or unsigned.
- In Java, the compiler represents the signed integers using [2's complement notation](https://en.wikipedia.org/wiki/Two%27s_complement). Therefore, in **Example 3**, the input represents the signed integer. `-3`.
# Solution Complexity
- $O(logn)$ time complexity
- $O(1)$ time complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def hammingWeight(self, n: int) -> int:
		ret = 0

		while n != 0:
			n &= (n - 1)
			ret += 1

		return ret
```