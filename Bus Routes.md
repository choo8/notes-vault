You are given an array `routes` representing bus routes where `routes[i]` is a bus route that the `ith` bus repeats forever.

- For example, if `routes[0] = [1, 5, 7]`, this means that the `0th` bus travels in the sequence `1 -> 5 -> 7 -> 1 -> 5 -> 7 -> 1 -> ...` forever.

You will start at the bus stop `source` (You are not on any bus initially), and you want to go to the bus stop `target`. You can travel between bus stops by buses only.

Return _the least number of buses you must take to travel from_ `source` _to_ `target`. Return `-1` if it is not possible.
# Solution Complexity
- $O(nk)$ time complexity
- $O(nk)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from collections import deque

class Solution:
	def numBusesToDestination(self, routes: List[List[int]], source: int, target: int) -> int:
		if source == target:
			return 0

		stop_to_buses = {}
		for bus_idx, route in enumerate(routes):
			for stop in route:
				if stop not in stop_to_buses:
					stop_to_buses[stop] = set()
				stop_to_buses[stop].add(bus_idx)

		if source not in stop_to_buses or target not in stop_to_buses:
			return -1

		parents, children, buses_taken, stops_visited, num_stops = deque(), deque(), set(), set(), 1
		for bus in stop_to_buses[source]:
			parents.append(bus)

		while len(parents) > 0:
			cur_bus = parents.popleft()
			buses_taken.add(cur_bus)

			if target in routes[cur_bus]:
				return num_stops

			for stop in routes[cur_bus]:
				if stop in stops_visited:
					continue
				stops_visited.add(stop)
				
				for bus in stop_to_buses[stop]:
					if bus not in buses_taken:
						children.append(bus)

			if len(parents) == 0:
				parents, children = children, deque()
				num_stops += 1

		return -1
```