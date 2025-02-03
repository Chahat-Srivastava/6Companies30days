## Question : Find the Distance Value between two arrays

### Problem Statement:
Given two integer arrays arr1 and arr2, and the integer d, return the distance value between the two arrays.

The distance value is defined as the number of elements arr1[i] such that there is not any element arr2[j] where |arr1[i]-arr2[j]| <= d.

### Code (Python):
```python
class Solution:
    def findTheDistanceValue(self, arr1: List[int], arr2: List[int], d: int) -> int:
        arr2.sort()
        count=0
        for i in range(len(arr1)):
            left=0
            right=len(arr2)-1
            while left<=right:
                mid=(left+right)//2
                if abs(arr2[mid]-arr1[i])<=d:
                    count+=1
                    break
                elif arr1[i]<arr2[mid]:
                    right=mid-1
                else:
                    left=mid+1
        return len(arr1)-count
        
        
