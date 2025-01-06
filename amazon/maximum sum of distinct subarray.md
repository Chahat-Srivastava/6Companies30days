## Question : Maximum Sum of Distinct Subarray with Length K

### Problem Statement:
You are given an integer array nums and an integer k. Find the maximum subarray sum of all the subarrays of nums that meet the following conditions:

The length of the subarray is k, and
All the elements of the subarray are distinct.
Return the maximum subarray sum of all the subarrays that meet the conditions. If no subarray meets the conditions, return 0.

A subarray is a contiguous non-empty sequence of elements within an array.
 
### Code (Python):
```python
class Solution:
    def maximumSubarraySum(self, nums: List[int], k: int) -> int:
        sum1=0
        dict1={}
        maxi=float('-inf')
        for i in range(k):
            sum1+=nums[i]
            if nums[i] in dict1:
                dict1[nums[i]]+=1
            else:
                dict1[nums[i]]=1
            if len(dict1)==k:
                maxi=max(maxi,sum1)
        for i in range(1,len(nums)-k+1):
            sum1=sum1-nums[i-1]+nums[i+k-1]
            if dict1[nums[i-1]]>1:
                dict1[nums[i-1]]-=1
            else:
                del dict1[nums[i-1]]
            if nums[i+k-1] in dict1:
                dict1[nums[i+k-1]]+=1
            else:
                dict1[nums[i+k-1]]=1 
            if len(dict1)==k:
                maxi=max(sum1,maxi)
        if maxi==float('-inf'):
            return 0
        else:
            return maxi

        
        
