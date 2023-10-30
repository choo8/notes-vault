Implement the `RandomizedSet` class:

- `RandomizedSet()` Initializes the `RandomizedSet` object.
- `bool insert(int val)` Inserts an item `val` into the set if not present. Returns `true` if the item was not present, `false` otherwise.
- `bool remove(int val)` Removes an item `val` from the set if present. Returns `true` if the item was present, `false` otherwise.
- `int getRandom()` Returns a random element from the current set of elements (it's guaranteed that at least one element exists when this method is called). Each element must have the **same probability** of being returned.

You must implement the functions of the class such that each function works in **average** `O(1)` time complexity.
# Solution Complexity
- $O(1)$ time complexity for `insert`, `remove` and `getRandom`
- $O(n)$ space complexity
# Thought Process
# Solution
- afda
```Python
import random

class RandomizedSet:
	def __init__(self):
		self.data_hash = {}
		self.data_list = []
		self.num_elements = 0

	def insert(self, val: int) -> bool:
		if val in self.data_hash:
			return False
		else:
			self.data_hash[val] = self.num_elements
			self.num_elements += 1
			self.data_list.append(val)

			return True

	def remove(self, val: int) -> bool:
		if val not in self.data_hash:
			return False
		else:
			self.data_hash[self.data_list[self.num_elements - 1]] = self.data_hash[val]
			self.data_list[self.data_hash[val]] = self.data_list[self.num_elements - 1]
			self.data_list.pop()
			del self.data_hash[val]
			self.num_elements -= 1
			return True

	def getRandom(self) -> int:
		return random.choice(self.data_list)
```