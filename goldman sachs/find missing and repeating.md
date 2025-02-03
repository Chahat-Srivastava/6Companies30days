## Question : Find Missing and Repeating

### Problem Statement:
Given an unsorted array arr of positive integers. One number a from the set [1, 2,....,n] is missing and one number b occurs twice in the array. Find numbers a and b.

Note: The test cases are generated such that there always exists one missing and one repeating number within the range [1,n].

### Code (Python):
```python
class Solution:
    def findTwoElement( self,arr): 
        n=len(arr)
        expected=[i for i in range(1,n+1)]
        arr.sort()
        for i in range(len(arr)-1):
            if arr[i]==arr[i+1]:
                b=arr[i]
                arr[i]=float('inf')
                break
        arr.sort()
        for i in range(len(arr)):
            if arr[i]!=expected[i]:
                a=expected[i]
                break
        return [b,a]
