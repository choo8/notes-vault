We have `n` jobs, where every job is scheduled to be done from `startTime[i]` to `endTime[i]`, obtaining a profit of `profit[i]`.

You're given the `startTime`, `endTime` and `profit` arrays, return the maximum profit you can take such that there are no two jobs in the subset with overlapping time range.

If you choose a job that ends at time `X` you will be able to start another job that starts at time `X`.
# Solution Complexity
- $O(nlogn)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from bisect import bisect_right

class Solution:
	def jobScheduling(self, startTime: List[int], endTime: List[int], profit: List[int]) -> int:
		endTime, startTime, profit = zip(*sorted(zip(endTime, startTime, profit)))
		dp = [(endTime[0], profit[0])]

		for idx in range(1, len(startTime)):
			right = bisect_right(dp, startTime[idx], key=lambda x: x[0])
			if right - 1 >= 0:
				doJob = dp[right - 1][1] + profit[idx]
			else:
				doJob = profit[idx]

			if doJob > dp[-1][1]:
				dp.append((endTime[idx], doJob))

		return dp[-1][1]
```