Design an algorithm to encode **a list of strings** to **a string**. The encoded string is then sent over the network and is decoded back to the original list of strings.

Machine 1 (sender) has the function:
```
string encode(vector<string> strs) {
  // ... your code
  return encoded_string;
}
```

Machine 2 (receiver) has the function:
```
vector<string> decode(string s) {
  //... your code
  return strs;
}
```

So Machine 1 does:
`string encoded_string = encode(strs);`

and Machine 2 does:
`vector<string> strs2 = decode(encoded_string);`

`strs2` in Machine 2 should be the same as `strs` in Machine 1.

Implement the `encode` and `decode` methods.

You are not allowed to solve the problem using any serialize methods (such as `eval`).
# Solution Complexity
- $O(nk)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Codec:
	def encode(self, strs: List[str]) -> str:
		"""Encodes a list of strings to a single string.
		"""
		return "".join([str(len(s)).zfill(3) + s for s in strs])

	def decode(self, s: str) -> List[str]:
		"""Decodes a single string to a list of strings.
		"""
		strs, idx = [], 0
		while idx < len(s):
			s_len = int(s[idx:idx + 3])
			strs.append(s[idx + 3:idx + 3 + s_len])
			idx = idx + 3 + s_len
		return strs

# Your Codec object will be instantiated and called as such:
# codec = Codec()
# codec.decode(codec.encode(strs))
```