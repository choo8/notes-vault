Given an array of strings `strs`, group **the anagrams** together. You can return the answer in **any order**.

An **Anagram** is a word or phrase formed by rearranging the letters of a different word or phrase, typically using all the original letters exactly once.
# Solution Complexity
- $O(nklogk)$ time complexity
- $O(nk)$ space complexity
# Thought Process
# Solution
- asdsadasd
```Python
from collections import defaultdict

class Solution:
	def groupAnagrams(self, strs: List[str]) -> List[List[str]]:
		res = defaultdict(list)
		
		for s in strs:
			res["".join(sorted(s))].append(s)	

		return res.values()
```