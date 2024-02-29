The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this: (you may want to display this pattern in a fixed font for better legibility)

P   A   H   N
A P L S I I G
Y   I   R

And then read line by line: `"PAHNAPLSIIGYIR"`

Write the code that will take a string and make this conversion given a number of rows:

string convert(string s, int numRows);
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def convert(self, s: str, numRows: int) -> str:
		converted = []
		for row_idx in range(numRows):
			distance = 1 if numRows == 1 else (numRows - 1) * 2
			for c_idx in range(row_idx, len(s), distance):
				# Append characters from verticals
				converted.append(s[c_idx])
				# Only append second character from diagonal if not in first or last row
				if numRows > 1 and row_idx % (numRows - 1) != 0 and c_idx + distance  - (row_idx * 2) < len(s):
					converted.append(s[c_idx + distance  - (row_idx * 2)])
		return "".join(converted)
```