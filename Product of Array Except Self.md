Given an integer array `nums`, return _an array_ `answer` _such that_ `answer[i]` _is equal to the product of all the elements of_ `nums` _except_ `nums[i]`.

The product of any prefix or suffix of `nums` is **guaranteed** to fit in a **32-bit** integer.

You must write an algorithm that runs in `O(n)` time and without using the division operation.

**Follow up:** Can you solve the problem in `O(1)` extra space complexity? (The output array **does not** count as extra space for space complexity analysis.)
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
- The bruteforce solution is to calculate each possible product via a nested for loop, resulting in an algorithm with a $O(n^2)$ time complexity and $O(1)$ space complexity, since we are not allowed to use the division operation (else we could just calculate the product of the entire array in $O(n)$ time and iterate the `nums` array in $O(n)$ time, dividing the total product during each index) the output array does not count as extra space complexity.
- To improve on the naïve solution, we can do away with the nested for loop by caching some pre-computations by iterating the `nums` array in $O(n)$ time complexity. As we are not allowed to use the division operation, we can pre-compute the prefix and suffix products of the array, where `prefix_product[i]` and `suffix_product[i]` are prefix and suffix products of the array, excluding `nums[i]`. Hence, after the pre-computation, we can iterate over the array once, and compute `answer[i]`, which is `prefix_product[i] * suffix_product[i]`.
- To further improve upon the optimized solution, we can remove the $O(n)$ space complexity requirement by doing away with `prefix_product` and `suffix_product` arrays. Instead, we first perform the pre-computation of `prefix_product` directly on the `answer` array, and thereafter iterate the array from the back while tracking a running `suffix_product` in a 32-bit integer variable (takes up additional $O(1)$ space complexity), and computing the answer, `nums[i] * suffix_product`.
# Solution
- Iterate `nums` once through, to compute the prefix product. Iterate the `nums` array once again from the back, while keeping track a running suffix product in a 32-bit integer variable, and calculate the answer, `nums[i] * suffix_product`
```Python
class Solution:
    def productExceptSelf(self, nums: List[int]) -> List[int]:
	    suffix_product = 1
	    res = [1] * len(nums)
	    
	    for idx in range(1, len(nums)):
		    res[idx] = res[idx - 1] * nums[idx - 1]
		
		for idx in range(len(nums) - 1, -1, -1):
			res[idx] = res[idx] * suffix_product
			suffix_product *= nums[idx]
		
		return res
```
```C++
class Solution {
public:
    vector<int> productExceptSelf(vector<int>& nums) {
        vector<int> res;

        for (int idx = 1; idx < nums.size(); idx++) {
            res.push_back()
        }
    }
};
```