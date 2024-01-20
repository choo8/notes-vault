Given a characters array `tasks`, representing the tasks a CPU needs to do, where each letter represents a different task. Tasks could be done in any order. Each task is done in one unit of time. For each unit of time, the CPU could complete either one task or just be idle.

However, there is a non-negative integer `n` that represents the cooldown period between two **same tasks** (the same letter in the array), that is that there must be at least `n` units of time between any two same tasks.

Return _the least number of units of times that the CPU will take to finish all the given tasks_.
# Solution Complexity
- $O(nklogk)$ time complexity
- $O(k)$ space complexity
# Thought Process
# Solution
- asdsad
```Python
from collections import Counter
import heapq

class Solution:
	def leastInterval(self, tasks: List[str], n: int) -> int:
		num_time = 0
		task_counter = Counter(tasks)
		heap = [(-task_counter[task], 0, task) for task in task_counter]
		heapq.heapify(heap)

		while len(heap) > 0:
			temp, done_task = [], False

			while len(heap) > 0:
				num_tasks, cur_n, cur_task = heapq.heappop(heap)

				if cur_n == 0:
					if not done_task:
						done_task = True

						if num_tasks + 1 < 0:
							temp.append((num_tasks + 1, n, cur_task))
					else:
						temp.append((num_tasks, cur_n, cur_task))
				else:
					temp.append((num_tasks, cur_n - 1, cur_task))

			heapq.heapify(temp)
			heap = temp
			num_time += 1

		return num_time
```