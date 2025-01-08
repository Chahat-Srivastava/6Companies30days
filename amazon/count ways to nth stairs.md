## Question : Count Ways to Nth Stairs

### Problem Statement:
You are given a non-negative integer k. There exists a staircase with an infinite number of stairs, with the lowest stair numbered 0.

Alice has an integer jump, with an initial value of 0. She starts on stair 1 and wants to reach stair k using any number of operations. If she is on stair i, in one operation she can:

Go down to stair i - 1. This operation cannot be used consecutively or on stair 0.
Go up to stair i + 2jump. And then, jump becomes jump + 1.
Return the total number of ways Alice can reach stair k.

Note that it is possible that Alice reaches the stair k, and performs some operations to reach the stair k again.
### Code (Python):
```python
class Solution:
    def waysToReachStair(self, k: int) -> int:
        target=k
        current_sum = 1
        ways = 0
        
        if target == 0 or target == 1:
            ways += 1
        
        pas = [[0] * 50 for _ in range(50)]
        pas[0][0] = 1
        
        for row in range(1, 50):
            pas[row][0] = 1
            for col in range(1, row + 1):
                pas[row][col] = pas[row - 1][col] + pas[row - 1][col - 1]

        for i in range(30):
            current_sum += 1 << i
            if current_sum >= target and current_sum - target <= i + 2:
                n = i + 2
                r = current_sum - target
                ways += pas[n][r]

        return ways
        
