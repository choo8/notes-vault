Given an integer `x`, return `true` _if_ `x` _is a **palindrome**, and_ `false` _otherwise_.
# Solution Complexity
- $O(logn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asd
```Python
class Solution:
	def isPalindrome(self, x: int) -> bool:
		if x < 0:
			return False

		reversed_x, tmp = 0, x

		while tmp >= 10:
			cur = tmp % 10
			tmp = tmp // 10

			reversed_x = reversed_x + cur
			reversed_x = reversed_x * 10

		return (reversed_x + tmp) == x
```