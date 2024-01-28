There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [ai, bi]` indicates that you **must** take course `bi` first if you want to take course `ai`.

- For example, the pair `[0, 1]`, indicates that to take course `0` you have to first take course `1`.

Return _the ordering of courses you should take to finish all courses_. If there are many valid answers, return **any** of them. If it is impossible to finish all courses, return **an empty array**.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Solution
- asdasd
```Python
from collections import deque

class Solution:
	def findOrder(self, numCourses: int, prerequisites: List[List[int]]) -> List[int]:
		graph = {}

		for course in range(numCourses):
			graph[course] = {"parents": 0, "children": set()}

		for post, pre in prerequisites:
			graph[post]["parents"] += 1
			graph[pre]["children"].add(post)

		ret, queue = [], deque()

		for course in graph:
			if graph[course]["parents"] == 0:
				queue.append(course)

		while len(queue) > 0:
			cur_course = queue.popleft()
			ret.append(cur_course)

			for child in graph[cur_course]["children"]:
				graph[child]["parents"] -= 1

				if graph[child]["parents"] == 0:
					queue.append(child)

		return ret if len(ret) == numCourses else []
```