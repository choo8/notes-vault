We are given `n` different types of `stickers`. Each sticker has a lowercase English word on it.

You would like to spell out the given string `target` by cutting individual letters from your collection of stickers and rearranging them. You can use each sticker more than once if you want, and you have infinite quantities of each sticker.

Return _the minimum number of stickers that you need to spell out_ `target`. If the task is impossible, return `-1`.

**Note:** In all test cases, all words were chosen randomly from the `1000` most common US English words, and `target` was chosen as a concatenation of two random words.
# Solution Complexity
- $O(n2^m)$ time complexity
- $O(2^m)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def minStickers(self, stickers: List[str], target: str) -> int:
		num_stickers = self._dfs(stickers, target, 0, {})
		return num_stickers if num_stickers != float("inf") else -1

	def _dfs(self, stickers: List[str], target: str, idx: int, memo: Dict) -> int:
		if target == "":
			return 0

		if idx == len(stickers):
			return float("inf")

		if (idx, target) in memo:
			return memo[(idx, target)]

		# Don't use current sticker
		num_stickers = self._dfs(stickers, target, idx + 1, memo)

		# Use current sticker
		cur_sticker = stickers[idx]
		cur_target = target
		removed = False
		for c in cur_sticker:
			idx_to_remove = cur_target.find(c)
			if idx_to_remove != -1:
				cur_target = cur_target[:idx_to_remove] + cur_target[idx_to_remove + 1:]
				removed = True

		if removed:
			num_stickers = min(num_stickers, 1 + self._dfs(stickers, cur_target, idx, memo))

		memo[(idx, target)] = num_stickers
		return num_stickers
```