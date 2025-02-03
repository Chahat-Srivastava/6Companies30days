## Question : People Aware of a Secret

### Problem Statement:
On day 1, one person discovers a secret.

You are given an integer delay, which means that each person will share the secret with a new person every day, starting from delay days after discovering the secret. You are also given an integer forget, which means that each person will forget the secret forget days after discovering it. A person cannot share the secret on the same day they forgot it, or on any day afterwards.

Given an integer n, return the number of people who know the secret at the end of day n. Since the answer may be very large, return it modulo 109 + 7.

### Code (Python):
```python
class Solution:
    def peopleAwareOfSecret(self, n: int, delay: int, forget: int) -> int:
        dp, md = [1] + [0] * (forget - 1), 10**9 + 7
        for i in range(1, n):
            dp[i % forget] = (md + dp[(i + forget - delay) % forget] - dp[i % forget] + (0 if i == 1 else dp[(i - 1) % forget])) % md
        return sum(dp) % md
