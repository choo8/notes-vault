Design a data structure that follows the constraints of a **[Least Recently Used (LRU) cache](https://en.wikipedia.org/wiki/Cache_replacement_policies#LRU)**.

Implement the `LRUCache` class:

- `LRUCache(int capacity)` Initialize the LRU cache with **positive** size `capacity`.
- `int get(int key)` Return the value of the `key` if the key exists, otherwise return `-1`.
- `void put(int key, int value)` Update the value of the `key` if the `key` exists. Otherwise, add the `key-value` pair to the cache. If the number of keys exceeds the `capacity` from this operation, **evict** the least recently used key.

The functions `get` and `put` must each run in `O(1)` average time complexity.
# Solution Complexity
- $O(1)$ time complexity for operations `get` and `put`
- $O(n)$ space complexity
# Thought Process
# Solution
- adasd
```Python
class Node:
	def __init__(self, key: int, val: int):
		self.key = key
		self.val = val
		self.flink = None
		self.blink = None

class LRUCache:
	def __init__(self, capacity: int):
		self.capacity = capacity
		self.num_keys = 0
		self.node_dict = {}
		self.list_head = Node(-1, -1)
		self.list_tail = Node(-2, -2)

		self.list_head.flink = self.list_tail
		self.list_tail.blink = self.list_head

	def get(self, key: int) -> int:
		if key in self.node_dict:
			val = self.node_dict[key].val
			self._removeNode(self.node_dict[key])
			new_node = self._insertHead(key, val)
			self.node_dict[key] = new_node

			return self.node_dict[key].val
		else:
			return -1

	def put(self, key: int, value: int) -> None:
		if key in self.node_dict:
			self._removeNode(self.node_dict[key])
		else:
			if self.num_keys == self.capacity:
				self._removeTail()
				self.num_keys -= 1
			self.num_keys += 1

		new_node = self._insertHead(key, value)
		self.node_dict[key] = new_node

	def _insertHead(self, key: int, val: int) -> Node:
		new_node = Node(key, val)
		self.list_head.flink.blink = new_node
		new_node.flink = self.list_head.flink
		self.list_head.flink = new_node
		new_node.blink = self.list_head

		return new_node

	def _removeNode(self, node: Node) -> None:
		node.flink.blink = node.blink
		node.blink.flink = node.flink
		
		del self.node_dict[node.key]

	def _removeTail(self) -> None:
		tail = self.list_tail.blink
		tail.blink.flink = self.list_tail
		self.list_tail.blink = tail.blink
		
		del self.node_dict[tail.key]
```