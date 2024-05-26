Given two sparse vectors, compute their dot product.

Implement class `SparseVector`:

- `SparseVector(nums)` Initializes the object with the vector `nums`
- `dotProduct(vec)` Compute the dot product between the instance of _SparseVector_ and `vec`

A **sparse vector** is a vector that has mostly zero values, you should store the sparse vector **efficiently** and compute the dot product between two _SparseVector_.

**Follow up:** What if only one of the vectors is sparse?
# Solution Complexity
- $O(k)$ time complexity
- $O(k)$ space complexity
# Thought Process
# Solution
- asdasd
```Python
class IndexNodes:
	def __init__(self, val: int):
		self.val = val
		self.next = None

class SparseVector:
	def __init__(self, nums: List[int]):
		self.indices = None
		self.weights = {}
		cur_idx = None
		for idx, n in enumerate(nums):
			if n != 0:
				if not self.indices:
					self.indices = IndexNodes(idx)
					cur_idx = self.indices
				else:
					cur_idx.next = IndexNodes(idx)
					cur_idx = cur_idx.next
				self.weights[idx] = n

    # Return the dotProduct of two sparse vectors
	def dotProduct(self, vec: 'SparseVector') -> int:
		dot_product = 0
		cur_idx, arg_idx = self.indices, vec.indices
		while cur_idx:
			if cur_idx.val in vec.weights:
				dot_product += self.weights[cur_idx.val] * vec.weights[cur_idx.val]
			cur_idx = cur_idx.next
		return dot_product

# Your SparseVector object will be instantiated and called as such:
# v1 = SparseVector(nums1)
# v2 = SparseVector(nums2)
# ans = v1.dotProduct(v2)
```