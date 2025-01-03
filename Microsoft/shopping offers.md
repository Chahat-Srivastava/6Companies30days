## Question : Shopping Offers

### Problem Statement:
In LeetCode Store, there are n items to sell. Each item has a price. However, there are some special offers, and a special offer consists of one or more different kinds of items with a sale price.

You are given an integer array price where price[i] is the price of the ith item, and an integer array needs where needs[i] is the number of pieces of the ith item you want to buy.

You are also given an array special where special[i] is of size n + 1 where special[i][j] is the number of pieces of the jth item in the ith offer and special[i][n] (i.e., the last integer in the array) is the price of the ith offer.

Return the lowest price you have to pay for exactly certain items as given, where you could make optimal use of the special offers. You are not allowed to buy more items than you want, even if that would lower the overall price. You could use any of the special offers as many times as you want.

 

 
### Code (Python):
```python
class Solution:
    def shoppingOffers(self, price: List[int], special: List[List[int]], needs: List[int]) -> int:
        return self.dp(price,special,needs,{})
    def dp(self,prices,specials,needs,memo):
        if tuple(needs) in memo:
            return memo[tuple(needs)]
        cost=sum(prices[i]*needs[i] for i in range(len(prices)))
        for offer in specials:
            updated_needs,valid=[],True
            for j in range(len(needs)):
                need=needs[j]-offer[j]
                if need<0:
                    valid=False
                    break
                updated_needs.append(need)
            if valid:
                cost=min(cost,offer[-1]+self.dp(prices,specials,updated_needs,memo))
        memo[tuple(needs)]=cost
        return cost
