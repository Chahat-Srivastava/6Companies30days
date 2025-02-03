## Question : Length of Longest Subarray with At most K Frequencies

### Problem Statement:
You are given an integer array nums and an integer k.

The frequency of an element x is the number of times it occurs in an array.

An array is called good if the frequency of each element in this array is less than or equal to k.

Return the length of the longest good subarray of nums.

A subarray is a contiguous non-empty sequence of elements within an array.

### Code (Python):
```python
class Solution:
    def maxSubarrayLength(self, nums: List[int], k: int) -> int:
        ans=0
        count={}
        left=0
        n=len(nums)
        for i in range(n):
            count[nums[i]] = count.get(nums[i],0)+1
            if count[nums[i]] > k:
                while nums[left] != nums[i]:
                    count[nums[left]]-=1
                    left+=1
                count[nums[left]]-=1
                left+=1
            ans = max(ans, i-left+1)
        return ans
        
