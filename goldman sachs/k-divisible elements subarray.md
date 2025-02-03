## Question : K-divisible elements Subarray

### Problem Statement:
Given an integer array nums and two integers k and p, return the number of distinct subarrays, which have at most k elements that are divisible by p.

Two arrays nums1 and nums2 are said to be distinct if:

They are of different lengths, or
There exists at least one index i where nums1[i] != nums2[i].
A subarray is defined as a non-empty contiguous sequence of elements in an array.

### Code (Python):
```python
class Solution:
    def countDistinct(self, nums: List[int], k: int, p: int) -> int:
        ans=set()
        for i in range(len(nums)):
            count=0
            temp=""
            for j in range(i,len(nums)):
                if nums[j]%p==0:
                    count+=1
                temp+=str(nums[j])+","
                if count>k:
                    break
                ans.add(temp)
        return len(ans)
