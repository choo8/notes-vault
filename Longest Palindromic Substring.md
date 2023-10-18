Given a string `s`, return _the longest palindromic substring_ in `s`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
- The bruteforce solution is to iterate over all possible substrings via nested for loops, and for each substring, check if they are palindromes, while keeping track of the longest palindrome found. This would result in an algorithm with $O(n^3)$ time complexity and $O(1)$ space complexity
- 
# Solution
- dfad
```Python
class Solution:
	def longestPalindrome(self, s: str) -> str:
		dp = [[0 for j in range(len(s))] for i in range(len(s))]
		max_string = ""

		for j in range(len(s)):
			for i in range(j + 1):
				if i == j:
					dp[i][j] = 1
					if j - i + 1 > len(max_string):
						max_string = s[i:j + 1]
				elif s[i] == s[j]:
					if i + 1 == j:
						dp[i][j] = 2
					elif dp[i + 1][j - 1] == j - i - 1:
						dp[i][j] = 2 + dp[i + 1][j - 1]
					if j - i + 1 > len(max_string):
						max_string = s[i:j + 1]
				else:
					dp[i][j] = 0
			
		return max_string
```
- asdasd
```Python
class Solution:
	def longestPalindrome(self, s: str) -> str:
		s_prime = "#"
		for c in s:
			s_prime += "|"
			s_prime += c
		s_prime += "|@"

		max_palindrome = ""
		radii = [0] *len(s_prime)
		center = 0
		max_right = 0
		max_len = 0
		palindrome_start = 0
		for i in range(1, len(s_prime) - 1):
			if i < max_right:
				radii[i] = min(max_right - i, radii[2 * center - i])

			while s_prime[i - radii[i] - 1] == s_prime[i + radii[i] + 1]:
				radii[i] += 1

			if i + radii[i] > max_right:
				center = i
				max_right = i + radii[i]

			if radii[i] > max_len:
				start = (i - radii[i] - 1) // 2
				max_len = radii[i]

		return s[start:start + max_len]
```