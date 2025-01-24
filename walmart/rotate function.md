## Question : Rotate Function

### Problem Statement:
You are given an integer array nums of length n.

Assume arrk to be an array obtained by rotating nums by k positions clock-wise. We define the rotation function F on nums as follow:

F(k) = 0 * arrk[0] + 1 * arrk[1] + ... + (n - 1) * arrk[n - 1].
Return the maximum value of F(0), F(1), ..., F(n-1).

The test cases are generated so that the answer fits in a 32-bit integer. 
### Code (Python):
```python
class Solution:
    def maxRotateFunction(self, nums: List[int]) -> int:
        r=curr=sum(i*j for i,j in enumerate(nums))
        s=sum(nums)
        k=len(nums)
        while nums:
            curr+=s-nums.pop()*k
            r=max(curr,r)
        return r
