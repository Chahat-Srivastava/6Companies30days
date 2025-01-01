## Question : Wiggle Sort II

### Problem Statement:
Given an integer array nums, reorder it such that nums[0] < nums[1] > nums[2] < nums[3]....

You may assume the input array always has a valid answer.

 

#### Example 1:

Input: nums = [1,5,1,1,6,4]
Output: [1,6,1,5,1,4]
Explanation: [1,4,1,5,1,6] is also accepted.
#### Example 2:

Input: nums = [1,3,2,2,3,1]
Output: [2,3,1,3,1,2]
### Code (Python):
```python
class Solution:
    def wiggleSort(self, nums: List[int]) -> None:
        """
        Do not return anything, modify nums in-place instead.
        """
        sorted_nums=sorted(nums)
        mid=(len(nums)+1)//2
        j,k=mid-1,len(nums)-1
        for i in range(len(nums)):
            if i%2==0:
                nums[i]=sorted_nums[j]
                j-=1
            else:
                nums[i]=sorted_nums[k]
                k-=1
                
