A string can be **abbreviated** by replacing any number of **non-adjacent**, **non-empty** substrings with their lengths. The lengths **should not** have leading zeros.

For example, a string such as `"substitution"` could be abbreviated as (but not limited to):

- `"s10n"` (`"s ubstitutio n"`)
- `"sub4u4"` (`"sub stit u tion"`)
- `"12"` (`"substitution"`)
- `"su3i1u2on"` (`"su bst i t u ti on"`)
- `"substitution"` (no substrings replaced)

The following are **not valid** abbreviations:

- `"s55n"` (`"s ubsti tutio n"`, the replaced substrings are adjacent)
- `"s010n"` (has leading zeros)
- `"s0ubstitution"` (replaces an empty substring)

Given a string `word` and an abbreviation `abbr`, return _whether the string **matches** the given abbreviation_.

A **substring** is a contiguous **non-empty** sequence of characters within a string.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def validWordAbbreviation(self, word: str, abbr: str) -> bool:
		word_idx, abbr_idx = 0, 0
		while word_idx < len(word) and abbr_idx < len(abbr):
			if abbr[abbr_idx].isalpha():
				if word[word_idx] == abbr[abbr_idx]:
					word_idx += 1
					abbr_idx += 1
				else:
					return False
			elif abbr[abbr_idx].isnumeric():
				# Leading zeros or empty substring
				if abbr[abbr_idx] == "0":
					return False
				cur_num = []
				while abbr_idx < len(abbr) and abbr[abbr_idx].isnumeric():
					cur_num.append(abbr[abbr_idx])
					abbr_idx += 1
				word_idx += int("".join(cur_num))

		return word_idx == len(word) and abbr_idx == len(abbr)
```