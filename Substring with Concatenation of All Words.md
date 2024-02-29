You are given a string `s` and an array of strings `words`. All the strings of `words` are of **the same length**.

A **concatenated substring** in `s` is a substring that contains all the strings of any permutation of `words` concatenated.

- For example, if `words = ["ab","cd","ef"]`, then `"abcdef"`, `"abefcd"`, `"cdabef"`, `"cdefab"`, `"efabcd"`, and `"efcdab"` are all concatenated strings. `"acdbef"` is not a concatenated substring because it is not the concatenation of any permutation of `words`.

Return _the starting indices of all the concatenated substrings in_ `s`. You can return the answer in **any order**.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import defaultdict
from copy import deepcopy

class Solution:
	def findSubstring(self, s: str, words: List[str]) -> List[int]:
		s_len, word_len, word_dict, window_dict, starting_indices = len(s), len(words[0]), defaultdict(int), defaultdict(int), []
		for word in words:
			word_dict[word] += 1
			window_dict[word] += 1

		left, right, substring_word_count = 0, 0, 0
		while True:
			# Current window contains substring with concatenation of all words
			if substring_word_count == len(words):
				starting_indices.append(left)
				window_dict, substring_word_count = deepcopy(word_dict), 0
				left += 1
				right = left
			elif right >= s_len:
				break
			# Current window does not contain any words
			elif left == right:
				if s[left:left + word_len] in window_dict:
					window_dict[s[left:left + word_len]] -= 1
					substring_word_count += 1
					right += word_len
				else:
					left += 1
					right += 1
			# Current window contains substring with concatenation of some words
			else:
				if s[right:right + word_len] in window_dict and window_dict[s[right:right + word_len]] > 0:
					window_dict[s[right:right + word_len]] -= 1
					substring_word_count += 1
					right += word_len
				else:
					window_dict, substring_word_count = deepcopy(word_dict), 0
					left += 1
					right = left

		return starting_indices
```