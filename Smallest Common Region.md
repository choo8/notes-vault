You are given some lists of `regions` where the first region of each list includes all other regions in that list.

Naturally, if a region `x` contains another region `y` then `x` is bigger than `y`. Also, by definition, a region `x` contains itself.

Given two regions: `region1` and `region2`, return _the smallest region that contains both of them_.

If you are given regions `r1`, `r2`, and `r3` such that `r1` includes `r3`, it is guaranteed there is no `r2` such that `r2` includes `r3`.

It is guaranteed the smallest region exists.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def findSmallestRegion(self, regions: List[List[str]], region1: str, region2: str) -> str:
		parents = {}

		for parent, *children in regions:
			for child in children:
				parents[child] = parent

		ancestors = set([region1])

		while region1 in parents:
			ancestors.add(parents[region1])
			region1 = parents[region1]

		while region2 in parents:
			if region2 in ancestors:
				return region2
			region2 = parents[region2]

		return region2
```