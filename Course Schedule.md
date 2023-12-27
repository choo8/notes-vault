There are a total of `numCourses` courses you have to take, labeled from `0` to `numCourses - 1`. You are given an array `prerequisites` where `prerequisites[i] = [ai, bi]` indicates that you **must** take course `bi` first if you want to take course `ai`.

- For example, the pair `[0, 1]`, indicates that to take course `0` you have to first take course `1`.

Return `true` if you can finish all courses. Otherwise, return `false`.
# Solution Complexity
- $O(n)$ time complexity
- $O(n^2)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
		graph, stack, num_edges = {}, [], 0
		visited = [False] * numCourses

		for idx in range(numCourses):
			graph[idx] = {"in": 0, "out": set()}

		for post_course, pre_course in prerequisites:
			graph[post_course]["in"] += 1
			graph[pre_course]["out"].add(post_course)
			num_edges += 1

		for course in graph.keys():
			if graph[course]["in"] == 0:
				stack.append(course)

		while len(stack) > 0:
			cur_course = stack.pop()

			for post_course in graph[cur_course]["out"]:
				graph[post_course]["in"] -= 1
				num_edges -= 1

				if graph[post_course]["in"] == 0:
					stack.append(post_course)

		if num_edges == 0:
			return True
		else:
			return False
```