Determine if a `9 x 9` Sudoku board is valid. Only the filled cells need to be validated **according to the following rules**:

1. Each row must contain the digits `1-9` without repetition.
2. Each column must contain the digits `1-9` without repetition.
3. Each of the nine `3 x 3` sub-boxes of the grid must contain the digits `1-9` without repetition.

**Note:**

- A Sudoku board (partially filled) could be valid but is not necessarily solvable.
- Only the filled cells need to be validated according to the mentioned rules.
# Solution Complexity
- $O(n^2)$ time complexity
- $O(n^2)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict

class Solution:
	def isValidSudoku(self, board: List[List[str]]) -> bool:
		rows, cols, boxes = [defaultdict(int) for _ in range(len(board))], [defaultdict(int) for _ in range(len(board[0]))], [defaultdict(int) for _ in range(int(len(board) / 3 * len(board[0]) / 3))]
		
		for r in range(len(board)):
			for c in range(len(board[0])):
				if board[r][c] == ".":
					continue

				if rows[r][board[r][c]] != 0 or cols[c][board[r][c]] != 0:
					return False
				else:
					rows[r][board[r][c]] += 1
					cols[c][board[r][c]] += 1

				r_box, c_box = r // 3, c // 3

				if boxes[r_box * 3 + c_box][board[r][c]] != 0:
					return False
				else:
					boxes[r_box * 3 + c_box][board[r][c]] += 1

		return True
```