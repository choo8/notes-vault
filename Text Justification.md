Given an array of strings `words` and a width `maxWidth`, format the text such that each line has exactly `maxWidth` characters and is fully (left and right) justified.

You should pack your words in a greedy approach; that is, pack as many words as you can in each line. Pad extra spaces `' '` when necessary so that each line has exactly `maxWidth` characters.

Extra spaces between words should be distributed as evenly as possible. If the number of spaces on a line does not divide evenly between words, the empty slots on the left will be assigned more spaces than the slots on the right.

For the last line of text, it should be left-justified, and no extra space is inserted between words.

**Note:**

- A word is defined as a character sequence consisting of non-space characters only.
- Each word's length is guaranteed to be greater than `0` and not exceed `maxWidth`.
- The input array `words` contains at least one word.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- sada
```Python
class Solution:
	def fullJustify(self, words: List[str], maxWidth: int) -> List[str]:
		if len(words) == 0:
			return []

		justified_words = []
		idx, cur_chars, cur_words = 0, len(words[0]), 1
		while True:
			# Append last line with left-justification
			if idx == len(words) - 1:
				cur_line = " ".join(words[len(words) - cur_words:])
				justified_words.append(cur_line + " " * (maxWidth - len(cur_line)))
				break
			# Check if another word can be fit into current line
			elif cur_chars + len(words[idx + 1]) + (cur_words - 1) + 1 <= maxWidth:
				cur_chars += len(words[idx + 1])
				cur_words += 1
				idx += 1
			# Append current line
			else:
				# Left justified if there is only 1 word in current line
				if cur_words == 1:
					cur_line = words[idx] + " " * (maxWidth - cur_chars)
				else:
					min_spaces, remainder_spaces = (maxWidth - cur_chars) // (cur_words - 1), (maxWidth - cur_chars) % (cur_words - 1)
					cur_line = []
					for word in words[idx - cur_words + 1:idx + 1]:
						cur_line.append(word)
						cur_line.append(" " * (min_spaces + 1) if remainder_spaces > 0 else " " * min_spaces)
						remainder_spaces -= 1
					cur_line = "".join(cur_line[:-1]) 
				justified_words.append(cur_line)
				cur_chars = len(words[idx + 1])
				cur_words = 1
				idx += 1

		return justified_words
```