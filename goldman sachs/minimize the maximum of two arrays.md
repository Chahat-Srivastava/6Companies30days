## Question : Minimize the Maximum of Two Arrays

### Problem Statement:
We have two arrays arr1 and arr2 which are initially empty. You need to add positive integers to them such that they satisfy all the following conditions:

arr1 contains uniqueCnt1 distinct positive integers, each of which is not divisible by divisor1.
arr2 contains uniqueCnt2 distinct positive integers, each of which is not divisible by divisor2.
No integer is present in both arr1 and arr2.
Given divisor1, divisor2, uniqueCnt1, and uniqueCnt2, return the minimum possible maximum integer that can be present in either array.

### Code (Python):
```python
class Solution:
    def gcd(self, a: int, b: int) -> int:
        while b:
            a, b = b, a % b
        return a
    def minimizeSet(self, divisor1: int, divisor2: int, uniqueCnt1: int, uniqueCnt2: int) -> int:
        l, r = 1, int(2 * 1e9)
        ans = r
        lcm = (divisor1 * divisor2) // self.gcd(divisor1, divisor2)
        while l <= r:
            mid = (l + r) // 2
            x = mid - mid // divisor1
            y = mid - mid // divisor2
            z = mid - mid // lcm
            if x < uniqueCnt1 or y < uniqueCnt2 or z < (uniqueCnt1 + uniqueCnt2):
                l = mid + 1
            else:
                ans = min(ans, mid)
                r = mid - 1
        
        return ans
