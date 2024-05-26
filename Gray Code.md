An **n-bit gray code sequence** is a sequence of `2n` integers where:

- Every integer is in the **inclusive** range `[0, 2n - 1]`,
- The first integer is `0`,
- An integer appears **no more than once** in the sequence,
- The binary representation of every pair of **adjacent** integers differs by **exactly one bit**, and
- The binary representation of the **first** and **last** integers differs by **exactly one bit**.

Given an integer `n`, return _any valid **n-bit gray code sequence**_.
# Solution Complexity
- $O(2^n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def grayCode(self, n: int) -> List[int]:
		code_seq = [0, 1]

		for i in range(2, n + 1):
			rev_seq = [code | (2 ** (i - 1)) for code in reversed(code_seq)]
			code_seq += rev_seq

		return code_seq
```