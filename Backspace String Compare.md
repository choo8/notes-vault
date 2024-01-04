Given two strings `s` and `t`, return `true` _if they are equal when both are typed into empty text editors_. `'#'` means a backspace character.

Note that after backspacing an empty text, the text will continue empty.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def backspaceCompare(self, s: str, t: str) -> bool:
		s_idx, t_idx = len(s) - 1, len(t) - 1
		s_count, t_count = 0, 0

		while True:
			while s_idx >= 0 and (s[s_idx] == "#" or s_count > 0):
				if s[s_idx] == "#":
					s_count += 1
				else:
					s_count -= 1
				s_idx -= 1
			while t_idx >= 0 and (t[t_idx] == "#" or t_count > 0):
				if t[t_idx] == "#":
					t_count += 1
				else:
					t_count -= 1
				t_idx -= 1
			if not (s_idx >= 0 and t_idx >= 0 and s[s_idx] == t[t_idx]):
				return s_idx == t_idx == -1
			s_idx -= 1
			t_idx -= 1
```