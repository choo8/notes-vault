Perform the following shift operations on a string:

- **Right shift**: Replace every letter with the **successive** letter of the English alphabet, where 'z' is replaced by 'a'. For example, `"abc"` can be right-shifted to `"bcd"` or `"xyz"` can be right-shifted to `"yza"`.
- **Left shift**: Replace every letter with the **preceding** letter of the English alphabet, where 'a' is replaced by 'z'. For example, `"bcd"` can be left-shifted to `"abc" or` `"yza"` can be left-shifted to `"xyz"`.

We can keep shifting the string in both directions to form an **endless** **shifting sequence**.

- For example, shift `"abc"` to form the sequence: `... <-> "abc" <-> "bcd" <-> ... <-> "xyz" <-> "yza" <-> ...`. `<-> "zab" <-> "abc" <-> ...`

You are given an array of strings `strings`, group together all `strings[i]` that belong to the same shifting sequence. You may return the answer in **any order**.
# Solution Complexity
- $O(nm)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict

class Solution:
	def groupStrings(self, strings: List[str]) -> List[List[str]]:
		group_dict = defaultdict(list)

		for s in strings:
			group_dict[self._getKey(s)].append(s)

		return [group for key, group in group_dict.items()]

	def _getKey(self, s: str) -> str:
		shift = ord(s[0]) - ord('a')
		return "".join([chr(((ord(c) - ord('a') - shift) % 26) + ord('a')) for c in s])
```