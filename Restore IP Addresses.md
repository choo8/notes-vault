A **valid IP address** consists of exactly four integers separated by single dots. Each integer is between `0` and `255` (**inclusive**) and cannot have leading zeros.

- For example, `"0.1.2.201"` and `"192.168.1.1"` are **valid** IP addresses, but `"0.011.255.245"`, `"192.168.1.312"` and `"192.168@1.1"` are **invalid** IP addresses.

Given a string `s` containing only digits, return _all possible valid IP addresses that can be formed by inserting dots into_ `s`. You are **not** allowed to reorder or remove any digits in `s`. You may return the valid IP addresses in **any** order.
# Solution Complexity
- $O()$ time complexity
- $O()$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def restoreIpAddresses(self, s: str) -> List[str]:
		self.valid_addresses = []
		self._helper(s, [])
		return self.valid_addresses

	def _helper(self, s: str, cur_address: List[str]) -> None:
		if len(s) == 0:
			if len(cur_address) == 4:
				self.valid_addresses.append(".".join(cur_address))
			return

		for num_digits in range(1, min(len(s) + 1, 4)):
			if int(s[:num_digits]) <= 255 and not (s[0] == "0" and num_digits > 1):
				self._helper(s[num_digits:], cur_address + [s[:num_digits]])
```