You are given an array `prices` where `prices[i]` is the price of a given stock on the `ith` day.

You want to maximize your profit by choosing a **single day** to buy one stock and choosing a **different day in the future** to sell that stock.

Return _the maximum profit you can achieve from this transaction_. If you cannot achieve any profit, return `0`.
# Solution Complexity
- $O(n)$ time complexity
- $O(1)$ space complexity
# Thought Process
- The bruteforce solution is to iterate all possible legal pairs `prices[i]` and `prices[j]`  (`i < j`) via nested for loops to get the pair with the maximum profit, resulting in a $O(n^2)$ time complexity algorithm, while having a $O(1)$ space complexity.
- To improve on the naïve solution, if we are able to reduce the tracking of all differences in stock prices, `prices[j] - prices[i]` where `i < j`, then we can reduce the time complexity. Since we only need to return the best possible profit, we can actually just track the lowest price seen and the best profit seen, which is the difference of the current price minus the lowest price seen.
# Solution
- Iterate the array while tracking the lowest price seen and the best profit seen, which is the largest difference between the current price and lowest price seen
```Python
class Solution:
	def maxProfit(self, prices: List[int]) -> int:
		best_profit = 0
		lowest_price_seen = prices[0]
	
		for price in prices:
			if price < lowest_price_seen:
				lowest_price_seen = price
			if price - lowest_price_seen > best_profit:
				best_profit = price - lowest_price_seen
		return best_profit
```
```C++
class Solution {
public:
    int maxProfit(vector<int>& prices) {
        int lowest_price_seen = INT_MAX;
        int best_profit = 0;
 
        for (auto price : prices) {
            lowest_price_seen = (price < lowest_price_seen) ? price : lowest_price_seen;
            best_profit = ((price - lowest_price_seen) > best_profit) ? price - lowest_price_seen : best_profit;
        }
        return best_profit;
    }
};
```