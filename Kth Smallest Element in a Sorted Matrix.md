Given an `n x n` `matrix` where each of the rows and columns is sorted in ascending order, return _the_ `kth` _smallest element in the matrix_.

Note that it is the `kth` smallest element **in the sorted order**, not the `kth` **distinct** element.

You must find a solution with a memory complexity better than `O(n^2)`.
# Solution Complexity
- $O(n^2)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- adasd
```Python
import heapq

class Solution:
    def kthSmallest(self, matrix: List[List[int]], k: int) -> int:
		heap = []

	    for i in range(len(matrix)):
		    for j in range(len(matrix[0])):
				heapq.heappush(heap, matrix[i][j])

		for _ in range(k):
			res = heapq.heappop(heap)

		return res
```