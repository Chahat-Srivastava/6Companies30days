## Question : Combination Sum

### Problem Statement:
Find all valid combinations of k numbers that sum up to n such that the following conditions are true:

Only numbers 1 through 9 are used.
Each number is used at most once.
Return a list of all possible valid combinations. The list must not contain the same combination twice, and the combinations may be returned in any order.

### Code (Python):
```python
class Solution:
    def combinationSum3(self, k: int, n: int) -> List[List[int]]:
        from itertools import combinations
        arr=[i for i in range(1,10)]
        output=list(combinations(arr,k))
        ans=[]
        for i in output:
            sum1=sum(i)
            if sum1==n:
                ans.append(list(i))
        return ans
