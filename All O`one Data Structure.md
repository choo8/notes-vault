Design a data structure to store the strings' count with the ability to return the strings with minimum and maximum counts.

Implement the `AllOne` class:

- `AllOne()` Initializes the object of the data structure.
- `inc(String key)` Increments the count of the string `key` by `1`. If `key` does not exist in the data structure, insert it with count `1`.
- `dec(String key)` Decrements the count of the string `key` by `1`. If the count of `key` is `0` after the decrement, remove it from the data structure. It is guaranteed that `key` exists in the data structure before the decrement.
- `getMaxKey()` Returns one of the keys with the maximal count. If no element exists, return an empty string `""`.
- `getMinKey()` Returns one of the keys with the minimum count. If no element exists, return an empty string `""`.

**Note** that each function must run in `O(1)` average time complexity.
# Solution Complexity
- $O(1)$ time complexity for `inc`, `dec`, `getMaxKey` and `getMinKey`
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasda
```Python
class Node:
	def __init__(self, key: str, count: int):
		self.key = key
		self.count = count
		self.flink = None
		self.blink = None

class AllOne:
	def __init__(self):
		self.node_dict = {}
		self.list_head = Node("LIST_HEAD", -1)
		self.list_tail = Node("LIST_TAIL", -1)

		self.list_head.flink = self.list_tail
		self.list_tail.blink = self.list_head

	def inc(self, key: str) -> None:
		if key not in self.node_dict:
			new_node = self._insertTail(key)
			self.node_dict[key] = new_node
		else:
			self._incNode(key)

	def dec(self, key: str) -> None:
		if self.node_dict[key].count == 1:
			self._removeNode(self.node_dict[key])
			del self.node_dict[key]
		else:
			self._decNode(key)

	def getMaxKey(self) -> str:
		if self.list_head.flink == self.list_tail:
			return ""
		else:
			return self.list_head.flink.key

	def getMinKey(self) -> str:
		if self.list_head.flink == self.list_tail:
			return ""
		else:
			return self.list_tail.blink.key

	def _insertTail(self, key: str) -> Node:
		new_node = Node(key, 1)
		new_node.flink = self.list_tail
		new_node.blink = self.list_tail.blink
		self.list_tail.blink = new_node
		new_node.blink.flink = new_node

		return new_node

	def _insertFrontOfNode(self, new_node: Node, old_node: Node) -> None:
		new_node.flink = old_node
		new_node.blink = old_node.blink
		old_node.blink = new_node
		new_node.blink.flink = new_node

	def _removeNode(self, node: Node) -> None:
		node.flink.blink = node.blink
		node.blink.flink = node.flink

	def _incNode(self, key: int) -> None:
		node = self.node_dict[key]
		node.count += 1

		while node.blink != self.list_head and node.count > node.blink.count:
			_temp = node.blink
			self._removeNode(node)
			self._insertFrontOfNode(node, _temp)

	def _decNode(self, key: int) -> None:
		node = self.node_dict[key]
		node.count -= 1

		while node.flink != self.list_tail and node.count < node.flink.count:
			_temp = node.flink
			self._removeNode(node)
			self._insertFrontOfNode(node, _temp.flink)
```