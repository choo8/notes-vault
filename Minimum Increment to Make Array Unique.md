You are given an integer array `nums`. In one move, you can pick an index `i` where `0 <= i < nums.length` and increment `nums[i]` by `1`.

Return _the minimum number of moves to make every value in_ `nums` _**unique**_.

The test cases are generated so that the answer fits in a 32-bit integer.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def minIncrementForUnique(self, nums: List[int]) -> int:
		# Counting sort
		arr = [0 for _ in range(10 ** 5 + 1)]
		for n in nums:
			arr[n] += 1

		num_increments = 0
		cur_left, cur_right, cur_sum, cur_nums = -1, 0, 0, 0
		for n, count in enumerate(arr):
			if count == 0:
				continue

			if cur_left == -1:
				cur_left = n

			if n > (cur_nums + cur_left - 1) + 1:
				print(n, cur_left, cur_sum, cur_nums)
				num_increments += int((cur_left + cur_left + cur_nums - 1) * (cur_nums / 2)) - cur_sum
				cur_left, cur_sum, cur_nums = n, 0, 0

			cur_sum += n * count
			cur_nums += count

		num_increments += int((cur_left + cur_left + cur_nums - 1) * (cur_nums / 2)) - cur_sum

		return num_increments
```