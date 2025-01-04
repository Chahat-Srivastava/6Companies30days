## Question : Count the Number of Irremovable Subarray

### Problem Statement:
You are given a 0-indexed array of positive integers nums.

A subarray of nums is called incremovable if nums becomes strictly increasing on removing the subarray. For example, the subarray [3, 4] is an incremovable subarray of [5, 3, 4, 6, 7] because removing this subarray changes the array [5, 3, 4, 6, 7] to [5, 6, 7] which is strictly increasing.

Return the total number of incremovable subarrays of nums.

Note that an empty array is considered strictly increasing.

A subarray is a contiguous non-empty sequence of elements within an array.
### Code (Python):
```python
class Solution:
    def helper_function(self,nums):
        for i in range(len(nums)-1):
            if nums[i]>=nums[i+1]:
                return False
        return True
    def incremovableSubarrayCount(self, nums: List[int]) -> int:
        n=len(nums)
        res=0
        for i in range(n):
            for j in range(i,n):
                left=nums[:i]
                right=nums[j+1:] if j<n-1 else []
                if self.helper_function(left+right):
                    res+=1
        return res
