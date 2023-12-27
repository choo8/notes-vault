Given an array of `points` where `points[i] = [xi, yi]` represents a point on the **X-Y** plane and an integer `k`, return the `k` closest points to the origin `(0, 0)`.

The distance between two points on the **X-Y** plane is the Euclidean distance (i.e., `√(x1 - x2)2 + (y1 - y2)2`).

You may return the answer in **any order**. The answer is **guaranteed** to be **unique** (except for the order that it is in).
# Solution Complexity
- $O(klogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
import heapq

class Point:
	def __init__(self, x: int, y: int):
		self.x = x
		self.y = y
		self.dist = float(x ** 2 + y ** 2) ** 0.5

	def __lt__(self, other):
		return self.dist < other.dist

class Solution:
	def kClosest(self, points: List[List[int]], k: int) -> List[List[int]]:
		heap = []

		for x, y in points:
			point = Point(x, y)
			heapq.heappush(heap, point)

		return [[point.x, point.y] for point in heapq.nsmallest(k, heap)]
```