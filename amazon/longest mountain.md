## Question : Longest Mountain

### Problem Statement:
You may recall that an array arr is a mountain array if and only if:

arr.length >= 3
There exists some index i (0-indexed) with 0 < i < arr.length - 1 such that:
arr[0] < arr[1] < ... < arr[i - 1] < arr[i]
arr[i] > arr[i + 1] > ... > arr[arr.length - 1]
Given an integer array arr, return the length of the longest subarray, which is a mountain. Return 0 if there is no mountain subarray.

 
### Code (Python):
```python
class Solution:
    def longestMountain(self, arr: List[int]) -> int:
        res=0
        for i in range(1,len(arr)-1):
            if arr[i-1]<arr[i]>arr[i+1]:
                l=r=i
                while l>0 and arr[l]>arr[l-1]:
                    l-=1
                while r+1<len(arr) and arr[r]>arr[r+1]:
                    r+=1
                res=max(res,(r-l+1))
        return res
        
