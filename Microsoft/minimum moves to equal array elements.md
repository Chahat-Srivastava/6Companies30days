## Question : Minimum Moves to Equal Array Elements

### Problem Statement:
Given an integer array nums of size n, return the minimum number of moves required to make all array elements equal.

In one move, you can increment or decrement an element of the array by 1.

Test cases are designed so that the answer will fit in a 32-bit integer.

 

#### Example 1:

Input: nums = [1,2,3]
Output: 2
Explanation:
Only two moves are needed (remember each move increments or decrements one element):
[1,2,3]  =>  [2,2,3]  =>  [2,2,2]
#### Example 2:

Input: nums = [1,10,2,9]
Output: 16
### Code (Python):
```python
class Solution:
    def minMoves2(self, nums: List[int]) -> int:
        nums.sort()
        sum1=0
        if len(nums)%2==1:
            avg=nums[len(nums)//2]
        else:
            avg=(nums[(len(nums)//2)-1]+nums[len(nums)//2])//2
        count=0
        for i in range(len(nums)):
            count+=abs(nums[i]-avg)
        return count
        
