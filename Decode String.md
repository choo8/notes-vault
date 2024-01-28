Given an encoded string, return its decoded string.

The encoding rule is: `k[encoded_string]`, where the `encoded_string` inside the square brackets is being repeated exactly `k` times. Note that `k` is guaranteed to be a positive integer.

You may assume that the input string is always valid; there are no extra white spaces, square brackets are well-formed, etc. Furthermore, you may assume that the original data does not contain any digits and that digits are only for those repeat numbers, `k`. For example, there will not be input like `3a` or `2[4]`.

The test cases are generated so that the length of the output will never exceed `105`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def decodeString(self, s: str) -> str:
		if len(s) == 0:
			return ""
		elif s[0] >= "0" and s[0] <= "9":
			end_idx = 1
			while end_idx < len(s) and s[end_idx] >= "0" and s[end_idx] <= "9":
				end_idx += 1

			k = int(s[:end_idx])

			end_str_idx, stack = end_idx + 1, 1
			while True:
				if s[end_str_idx] == "[":
					stack += 1
				elif s[end_str_idx] == "]":
					stack -= 1

				if stack == 0:
					break

				end_str_idx += 1

			return "".join([self.decodeString(s[end_idx + 1:end_str_idx])] * k) + self.decodeString(s[end_str_idx + 1:])
		else:
			end_idx = 1
			while end_idx < len(s) and not (s[end_idx] >= "0" and s[end_idx] <= "9"):
				end_idx += 1

			return s[:end_idx] + self.decodeString(s[end_idx:])
```