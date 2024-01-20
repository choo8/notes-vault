There are `n` gas stations along a circular route, where the amount of gas at the `ith` station is `gas[i]`.

You have a car with an unlimited gas tank and it costs `cost[i]` of gas to travel from the `ith` station to its next `(i + 1)th` station. You begin the journey with an empty tank at one of the gas stations.

Given two integer arrays `gas` and `cost`, return _the starting gas station's index if you can travel around the circuit once in the clockwise direction, otherwise return_ `-1`. If there exists a solution, it is **guaranteed** to be **unique**
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
class Solution:
	def canCompleteCircuit(self, gas: List[int], cost: List[int]) -> int:
		start_idx, cur_idx, cur_gas = 0, 0, 0

		while True:
			if cur_gas + gas[cur_idx] - cost[cur_idx] < 0:
				if (cur_idx + 1) % len(gas) <= start_idx:
					return -1
				start_idx = (cur_idx + 1) % len(gas)
				cur_idx = start_idx
				cur_gas = 0
			else:
				cur_gas += gas[cur_idx] - cost[cur_idx]
				cur_idx = (cur_idx + 1) % len(gas)
				if cur_idx == start_idx:
					return start_idx
```