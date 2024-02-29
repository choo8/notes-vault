Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

You may assume that each input would have **_exactly_ one solution**, and you may not use the _same_ element twice.

You can return the answer in any order.
# Solution Complexity
- $O(n)$ time complexity
- $O(n)$ space complexity
# Thought Process
- For the bruteforce solution, we can check all possible pairs against the target sum via a nested for loop, resulting in a $O(n^2)$ time complexity algorithm, while having a $O(1)$ space complexity
- To improve on the bruteforce solution, we have to try to obtain the information of the other elements of the list during the outer loop. If we are able to perform the check in the outer loop, we will not need the nested inner loop, reducing the time complexity of the algorithm
- [[Hash Tables]] are good for trading space for time complexity, providing $O(1)$ lookups at the cost of additional space. With [[Hash Tables]], we can cache the information of the previously traversed elements without needing a nested for loop. This allows us to perform the calculation in the bruteforce solution in a single loop, reducing the algorithm's time complexity from $O(n^2)$ to $O(n)$
# Solution
- Iterate the array while caching previously seen values and their indices in a [[Hash Tables]]
- For each element of the array, check if `target - n` exists in the [[Hash Tables]] and return the indices if found
```Python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
	    complements = {}
		for idx, n in enumerate(nums):
			if target - n in complements:
				return [complements[target - n], idx]
			else:
				complements[n] = idx
		return []
```
```C++
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        map<int, int> complements;
        vector<int> indices;

        for (auto idx = 0; idx < nums.size(); idx++) {
            if (auto search = complements.find(target - nums[idx]); search != complements.end()) {
                indices.push_back(complements[target - nums[idx]]);
                indices.push_back(idx);
                return indices;
            }
            complements[nums[idx]] = idx;
        }
        return indices;
    }
};
```
