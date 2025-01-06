## Question : Calculate Maximum Profit

### Problem Statement:
You are given an integer array prices where prices[i] is the price of a given stock on the ith day, and an integer k.

Find the maximum profit you can achieve. You may complete at most k transactions: i.e. you may buy at most k times and sell at most k times.

Note: You may not engage in multiple transactions simultaneously (i.e., you must sell the stock before you buy again).
### Code (Python):
```python
class Solution:
    def get_max_profit(self,prices,n,ind,buy,cap,dp):
        if ind==n or cap==0:
            return 0
        if dp[ind][buy][cap]!=-1:
            return dp[ind][buy][cap]
        profit=0
        if buy == 0:
            profit = max(0 + self.get_max_profit(prices, n, ind + 1, 0, cap, dp),
            -prices[ind] + self.get_max_profit(prices, n, ind + 1, 1, cap, dp))
        if buy == 1:
            profit = max(0 + self.get_max_profit(prices, n, ind + 1, 1, cap, dp),
            prices[ind] + self.get_max_profit(prices, n, ind + 1, 0, cap - 1, dp))
        dp[ind][buy][cap] = profit
        return profit
    def maxProfit(self, k: int, prices: List[int]) -> int:
        n=len(prices)
        dp = [[[(-1) for i in range(k + 1)] for j in range(2)] for l in range(n)]
        print(dp)
        return self.get_max_profit(prices, n, 0, 0, k, dp)
        
