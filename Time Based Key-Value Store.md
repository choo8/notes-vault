Design a time-based key-value data structure that can store multiple values for the same key at different time stamps and retrieve the key's value at a certain timestamp.

Implement the `TimeMap` class:

- `TimeMap()` Initializes the object of the data structure.
- `void set(String key, String value, int timestamp)` Stores the key `key` with the value `value` at the given time `timestamp`.
- `String get(String key, int timestamp)` Returns a value such that `set` was called previously, with `timestamp_prev <= timestamp`. If there are multiple such values, it returns the value associated with the largest `timestamp_prev`. If there are no values, it returns `""`.
# Solution Complexity
- $O(1)$ time complexity for `set` operation and $O(log n)$ time complexity for `get` operation
- $O(n)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class TimeMap:
	def __init__(self):
		self.store = {}

	def set(self, key: str, value: str, timestamp: int) -> None:
		if key not in self.store:
			self.store[key] = {"timestamps": [timestamp], "values": [value]}
		else:
			self.store[key]["timestamps"].append(timestamp)
			self.store[key]["values"].append(value)

	def get(self, key: str, timestamp: int) -> str:
		if key not in self.store or timestamp < self.store[key]["timestamps"][0]:
			return ""

		left, right = 0, len(self.store[key]["timestamps"]) - 1

		while left <= right:
			mid = left + (right - left) // 2

			if self.store[key]["timestamps"][mid] == timestamp:
				return self.store[key]["values"][mid]
			elif self.store[key]["timestamps"][mid] < timestamp:
				if (mid + 1 < len(self.store[key]["timestamps"])) and (timestamp < self.store[key]["timestamps"][mid + 1]):
					return self.store[key]["values"][mid]
				else:
					left = mid + 1
			else:
				right = mid - 1

		return self.store[key]["values"][right]
# Your TimeMap object will be instantiated and called as such:
# obj = TimeMap()
# obj.set(key,value,timestamp)
# param_2 = obj.get(key,timestamp)
```