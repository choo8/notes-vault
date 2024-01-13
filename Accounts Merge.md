Given a list of `accounts` where each element `accounts[i]` is a list of strings, where the first element `accounts[i][0]` is a name, and the rest of the elements are **emails** representing emails of the account.

Now, we would like to merge these accounts. Two accounts definitely belong to the same person if there is some common email to both accounts. Note that even if two accounts have the same name, they may belong to different people as people could have the same name. A person can have any number of accounts initially, but all of their accounts definitely have the same name.

After merging the accounts, return the accounts in the following format: the first element of each account is the name, and the rest of the elements are emails **in sorted order**. The accounts themselves can be returned in **any order**.
# Solution Complexity
- $O(mnlogn)$ time complexity
- $O(mn)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from collections import defaultdict

class Solution:
	def accountsMerge(self, accounts: List[List[str]]) -> List[List[str]]:
		self.email_to_account = defaultdict(list)
		self.visited_accounts = [False for _ in range(len(accounts))]
		res = []

		for account, (name, *emails) in enumerate(accounts):
			for email in emails:
				self.email_to_account[email].append(account)

		for idx, (name, *emails) in enumerate(accounts):
			if self.visited_accounts[idx]:
				continue

			emails_set = set()

			self.dfs(idx, accounts, emails_set)

			res.append([name] + sorted(emails_set))

		return res

	def dfs(self, account, accounts, emails_set):
		if self.visited_accounts[account]:
			return

		self.visited_accounts[account] = True

		for email in accounts[account][1:]:
			emails_set.add(email)

			for neighbor in self.email_to_account[email]:
				self.dfs(neighbor, accounts, emails_set)
```