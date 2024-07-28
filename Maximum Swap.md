You are given an integer `num`. You can swap two digits at most once to get the maximum valued number.

Return _the maximum valued number you can get_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def maximumSwap(self, num: int) -> int:
		num_str, max_dict = list(str(num)), {}
		idx = len(num_str) - 1

		while idx >= 0:
			if idx not in max_dict:
				max_dict[idx] = (int(num_str[idx]), idx)
			if idx < len(num_str) - 1 and max_dict[idx + 1][0] >= max_dict[idx][0]:
				max_dict[idx] = max_dict[idx + 1]
			idx -= 1

		for idx, c in enumerate(num_str):
			if int(c) < max_dict[idx][0]:
				num_str[idx], num_str[max_dict[idx][1]] = num_str[max_dict[idx][1]], num_str[idx]
				break

		return int("".join(num_str))
```