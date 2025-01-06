## Question : K Sized Subarray Maximum

### Problem Statement:
Given an array arr[] of integers and an integer k, your task is to find the maximum value for each contiguous subarray of size k. The output should be an array of maximum values corresponding to each contiguous subarray.
### Code (Python):
```python
class Solution:
    #Function to find maximum of each subarray of size k.
    def maxOfSubarrays(self, arr, k):
        from collections import deque
        dq=deque()
        ans=[]
        for i in range(len(arr)):
            if len(dq)!=0 and dq[0]==i-k:
                dq.popleft()
            while len(dq)!=0 and arr[dq[-1]]<arr[i]:
                dq.pop()
            dq.append(i)
            if i>=k-1:
                ans.append(arr[dq[0]])
        return ans
