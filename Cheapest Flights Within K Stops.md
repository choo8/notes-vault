There are `n` cities connected by some number of flights. You are given an array `flights` where `flights[i] = [fromi, toi, pricei]` indicates that there is a flight from city `fromi` to city `toi` with cost `pricei`.

You are also given three integers `src`, `dst`, and `k`, return _**the cheapest price** from_ `src` _to_ `dst` _with at most_ `k` _stops._ If there is no such route, return `-1`.
# Solution Complexity
- $O(ke)$ time complexity
- $O(kv)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
import sys

class Solution:
	def findCheapestPrice(self, n: int, flights: List[List[int]], src: int, dst: int, k: int) -> int:
		prices = [[sys.maxsize for _ in range(n)] for _ in range(k + 1)]
		prices[0][src] = 0
		for parent, child, price in flights:
			if parent == src:
				prices[0][child] = price

		for transfer in range(1, k + 1):
			for city in range(n):
				prices[transfer][city] = min(prices[transfer][city], prices[transfer - 1][city])

			for parent, child, price in flights:
				prices[transfer][child] = min(prices[transfer][child], prices[transfer - 1][parent] + price)

		return -1 if prices[k][dst] == sys.maxsize else prices[k][dst]
```