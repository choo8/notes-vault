Winter is coming! During the contest, your first job is to design a standard heater with a fixed warm radius to warm all the houses.

Every house can be warmed, as long as the house is within the heater's warm radius range. 

Given the positions of `houses` and `heaters` on a horizontal line, return _the minimum radius standard of heaters so that those heaters could cover all houses._

**Notice** that all the `heaters` follow your radius standard, and the warm radius will the same.
# Solution Complexity
- $O(nlogm)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdad
```Python
class Solution:
	def findRadius(self, houses: List[int], heaters: List[int]) -> int:
		houses.sort()
		heaters.sort()

		def _checkRadius(radius: int, houses: List[int], heaters: List[int]) -> bool:
			house_ptr, heater_ptr = 0, 0

			while house_ptr < len(houses) and heater_ptr < len(heaters):
				if (houses[house_ptr] < heaters[heater_ptr] - radius or houses[house_ptr] > heaters[heater_ptr] + radius):
					heater_ptr += 1
				else:
					house_ptr += 1

			return house_ptr == len(houses)

		left, right = 0, max(max(heaters) - min(houses), max(houses) - min(heaters))
		while left < right:
			print(left, right)
			mid = left + (right - left) // 2
			if _checkRadius(mid, houses, heaters):
				right = mid
			else:
				left = mid + 1

		return left
```