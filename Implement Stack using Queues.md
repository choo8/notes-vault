Implement a last-in-first-out (LIFO) stack using only two queues. The implemented stack should support all the functions of a normal stack (`push`, `top`, `pop`, and `empty`).

Implement the `MyStack` class:

- `void push(int x)` Pushes element x to the top of the stack.
- `int pop()` Removes the element on the top of the stack and returns it.
- `int top()` Returns the element on the top of the stack.
- `boolean empty()` Returns `true` if the stack is empty, `false` otherwise.

**Notes:**

- You must use **only** standard operations of a queue, which means that only `push to back`, `peek/pop from front`, `size` and `is empty` operations are valid.
- Depending on your language, the queue may not be supported natively. You may simulate a queue using a list or deque (double-ended queue) as long as you use only a queue's standard operations.
# Solution Complexity
- $O(n)$ time complexity for `push` operation, $O(1)$ time complexity for operations `pop`, `top` and `empty`
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
from collections import deque

class MyStack:
	def __init__(self):
		self.q1 = deque()
		self.q2 = deque()

	def push(self, x: int) -> None:
		while len(self.q1) > 0:
			self.q2.append(self.q1.popleft())

		self.q1.append(x)

		while len(self.q2) > 0:
			self.q1.append(self.q2.popleft())

	def pop(self) -> int:
		return self.q1.popleft()

	def top(self) -> int:
		return self.q1[0]

	def empty(self) -> bool:
		return len(self.q1) == 0
```