Given a string `s` which represents an expression, _evaluate this expression and return its value_. 

The integer division should truncate toward zero.

You may assume that the given expression is always valid. All intermediate results will be in the range of `[-231, 231 - 1]`.

**Note:** You are not allowed to use any built-in function which evaluates strings as mathematical expressions, such as `eval()`.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- adsad
```Python
class Solution:
	def calculate(self, s: str) -> int:
		pre_operation, mul_div_state = "+", False
		cur_num, cur_operation, cur_sum, res = 0, "+", 0, 0

		for c in s + "+":
			if c.isnumeric():
				cur_num = cur_num * 10 + int(c)
			elif c == " ":
				continue
			else:
				if c in {"+", "-"}:
					if mul_div_state:
						if pre_operation == "+":
							if cur_operation == "*":
								res += (cur_sum * cur_num)
							else:
								res += int(cur_sum / cur_num)
						else:
							if cur_operation == "*":
								res -= (cur_sum * cur_num)
							else:
								res -= int(cur_sum / cur_num)
					else:
						if cur_operation == "+":
							res += cur_num
						else:
							res -= cur_num
					pre_operation, mul_div_state = c, False
					cur_operation = c
				elif c in {"*", "/"}:
					if mul_div_state:
						if cur_operation == "*":
							cur_sum *= cur_num
						else:
							cur_sum = int(cur_sum / cur_num)
					else:
						pre_operation, mul_div_state = cur_operation, True
						cur_sum = cur_num
						   
				cur_operation = c
				cur_num = 0

		return res
```