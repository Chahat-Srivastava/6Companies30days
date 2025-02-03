## Question : The Number of Good Subsets

### Problem Statement:
You are given an integer array nums. We call a subset of nums good if its product can be represented as a product of one or more distinct prime numbers.

For example, if nums = [1, 2, 3, 4]:
[2, 3], [1, 2, 3], and [1, 3] are good subsets with products 6 = 2*3, 6 = 2*3, and 3 = 3 respectively.
[1, 4] and [4] are not good subsets with products 4 = 2*2 and 4 = 2*2 respectively.
Return the number of different good subsets in nums modulo 109 + 7.

A subset of nums is any array that can be obtained by deleting some (possibly none or all) elements from nums. Two subsets are different if and only if the chosen indices to delete are different.

### Code (Python):
```python
class Solution:
    def numberOfGoodSubsets(self, nums: List[int]) -> int:
        P = [2, 3, 5, 7, 11, 13, 17, 19, 23, 29]
        cnt = Counter(nums)
        bm = [sum(1<<i for i, p in enumerate(P) if x % p == 0) for x in range(31)]
        bad = set([4, 8, 9, 12, 16, 18, 20, 24, 25, 27, 28])
        M = 10**9 + 7
        
        @lru_cache(None)
        def dp(mask, num):
            if num == 1: return 1
            ans = dp(mask, num - 1)
            if num not in bad and mask | bm[num] == mask:
                ans += dp(mask ^ bm[num], num - 1) * cnt[num]
            return ans % M

        return ((dp(1023, 30) - 1) * pow(2, cnt[1], M)) % M
