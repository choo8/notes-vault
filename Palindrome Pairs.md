You are given a **0-indexed** array of **unique** strings `words`.

A **palindrome pair** is a pair of integers `(i, j)` such that:

- `0 <= i, j < words.length`,
- `i != j`, and
- `words[i] + words[j]` (the concatenation of the two strings) is a palindrome.

Return _an array of all the **palindrome pairs** of_ `words`.

You must write an algorithm with `O(sum of words[i].length)` runtime complexity.
# Solution Complexity
- $O(nk^2)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def palindromePairs(self, words: List[str]) -> List[List[int]]:
		rev_words, pairs = {}, []

		for idx, word in enumerate(words):
			rev_words[word[::-1]] = idx

		for idx, word in enumerate(words):
			if word in rev_words and idx != rev_words[word]:
				pairs.append([idx, rev_words[word]])

			if word != "" and "" in rev_words and word in rev_words and idx == rev_words[word]:
				pairs.append([idx, rev_words[""]])
				pairs.append([rev_words[""], idx])

			for word_idx in range(1, len(word)):
				if word[word_idx:] in rev_words and word[:word_idx] == "".join(reversed(word[:word_idx])):
					pairs.append([rev_words[word[word_idx:]], idx])
				if word[:word_idx] in rev_words and word[word_idx:] == "".join(reversed(word[word_idx:])):
					pairs.append([idx, rev_words[word[:word_idx]]])

		return pairs
```