## Question : Ways to Reach a Position After K steps

### Problem Statement:
You are given two positive integers startPos and endPos. Initially, you are standing at position startPos on an infinite number line. With one step, you can move either one position to the left, or one position to the right.

Given a positive integer k, return the number of different ways to reach the position endPos starting from startPos, such that you perform exactly k steps. Since the answer may be very large, return it modulo 109 + 7.

Two ways are considered different if the order of the steps made is not exactly the same.

Note that the number line includes negative integers.

### Code (Python):
```python
class Solution:
    def numberOfWays(self, startPos: int, endPos: int, k: int) -> int:
        from math import comb
        total_distance = abs(endPos - startPos)
        if (k - total_distance) % 2 != 0 or k < total_distance:
            return 0
        right_steps = (k - total_distance) // 2
        return comb(k, right_steps) % (10**9 + 7)
