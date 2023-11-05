Given an `m x n` `matrix`, return _all elements of the_ `matrix` _in spiral order_.
# Solution Complexity
- $O(mn)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def spiralOrder(self, matrix: List[List[int]]) -> List[int]:
	    cur_r, cur_c, cur_layer, state = 0, 0, 0, "RIGHT"
		res = []

		while len(res) != len(matrix) * len(matrix[0]):
			res.append(matrix[cur_r][cur_c])

			if state == "RIGHT":
				if cur_c == len(matrix[0]) - cur_layer - 1:
					cur_r += 1
					state = "DOWN"
				else:
					cur_c += 1
			elif state == "DOWN":
				if cur_r == len(matrix) - cur_layer - 1:
					cur_c -= 1
					state = "LEFT"
				else:
					cur_r += 1
			elif state == "LEFT":
				if cur_c == cur_layer:
					cur_r -= 1
					state = "UP"
				else:
					cur_c -= 1
			elif state == "UP":
				if cur_r == cur_layer + 1:
					cur_c += 1
					state = "RIGHT"
					cur_layer += 1
				else:
					cur_r -= 1

		return res
```