You are given two lists of closed intervals, `firstList` and `secondList`, where `firstList[i] = [starti, endi]` and `secondList[j] = [startj, endj]`. Each list of intervals is pairwise **disjoint** and in **sorted order**.

Return _the intersection of these two interval lists_.

A **closed interval** `[a, b]` (with `a <= b`) denotes the set of real numbers `x` with `a <= x <= b`.

The **intersection** of two closed intervals is a set of real numbers that are either empty or represented as a closed interval. For example, the intersection of `[1, 3]` and `[2, 4]` is `[2, 3]`.
# Solution Complexity
- $O(n + m)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def intervalIntersection(self, firstList: List[List[int]], secondList: List[List[int]]) -> List[List[int]]:
		first, second, intersections = 0, 0, []

		while first < len(firstList) and second < len(secondList):
			if self._isIntersect(firstList[first], secondList[second]):
				intersections.append(self._getIntersection(firstList[first], secondList[second]))

			if firstList[first][1] < secondList[second][1]:
				first += 1
			else:
				second += 1

		return intersections

	def _isIntersect(self, i1: List[int], i2: List[int]) -> bool:
		if i2[0] < i1[0]:
			i1, i2 = i2, i1
		return i1[1] >= i2[0]

	def _getIntersection(self, i1: List[int], i2: List[int]) -> List[int]:
		return [max(i1[0], i2[0]), min(i1[1], i2[1])]
```