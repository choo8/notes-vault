An image is represented by an `m x n` integer grid `image` where `image[i][j]` represents the pixel value of the image.

You are also given three integers `sr`, `sc`, and `color`. You should perform a **flood fill** on the image starting from the pixel `image[sr][sc]`.

To perform a **flood fill**, consider the starting pixel, plus any pixels connected **4-directionally** to the starting pixel of the same color as the starting pixel, plus any pixels connected **4-directionally** to those pixels (also with the same color), and so on. Replace the color of all of the aforementioned pixels with `color`.

Return _the modified image after performing the flood fill_.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class Solution:
	def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:
		stack = [(sr, sc)]
		visited = set()
		src_color = image[sr][sc]

		while len(stack) > 0:
			r, c = stack.pop()
			image[r][c] = color
			visited.add((r, c))

			for _r, _c in [(r - 1, c), (r + 1, c), (r, c - 1), (r, c + 1)]:
				if _r >= 0 and _r < len(image) and _c >= 0 and _c < len(image[0]) and (_r, _c) not in visited and image[_r][_c] == src_color:
					stack.append((_r, _c))

		return image
```