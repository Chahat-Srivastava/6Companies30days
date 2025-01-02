## Question : Count Number of Nice Subarray

### Problem Statement:
Given an array of integers nums and an integer k. A continuous subarray is called nice if there are k odd numbers on it.

Return the number of nice sub-arrays.
### Code (Python):
```python
class Solution:
    def numberOfSubarrays(self, nums: List[int], k: int) -> int:
        n=len(nums)
        for i in range(n):
            if nums[i]%2==0:
                nums[i]=0
            else:
                nums[i]=1
        prefix_sum=0
        count=0
        dict1={0:1}
        for i in range(n):
            prefix_sum+=nums[i]
            remove=prefix_sum-k
            if remove in dict1:
                count+=dict1[remove]
            if prefix_sum in dict1:
                dict1[prefix_sum]+=1
            else:
                dict1[prefix_sum]=1
        return count
