We are given an array `asteroids` of integers representing asteroids in a row.

For each asteroid, the absolute value represents its size, and the sign represents its direction (positive meaning right, negative meaning left). Each asteroid moves at the same speed.

Find out the state of the asteroids after all collisions. If two asteroids meet, the smaller one will explode. If both are the same size, both will explode. Two asteroids moving in the same direction will never meet.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def asteroidCollision(self, asteroids: List[int]) -> List[int]:
		stack = []

		for a in asteroids:
			if len(stack) == 0:
				stack.append(a)
			else:
				while len(stack) > 0:
					if stack[-1] > 0 and a < 0:
						if abs(a) == abs(stack[-1]):
							stack.pop()
							break
						elif abs(a) > abs(stack[-1]):
							stack.pop()

							if len(stack) == 0:
								stack.append(a)
								break
						else:
							break
					else:
						stack.append(a)
						break

		return stack
```