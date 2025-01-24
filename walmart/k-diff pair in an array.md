## Question : K-diff Pairs in an Array

### Problem Statement:
Given an array of integers nums and an integer k, return the number of unique k-diff pairs in the array.

A k-diff pair is an integer pair (nums[i], nums[j]), where the following are true:

0 <= i, j < nums.length
i != j
|nums[i] - nums[j]| == k
Notice that |val| denotes the absolute value of val.
### Code (Python):
```python
class Solution:
    def findPairs(self, nums: List[int], k: int) -> int:
        dict1={}
        if k>0:
            ans=set()
            temp=set(nums)
            for i in temp:
                dict1[i]=1
            for i in temp:
                if i>0:
                    t=k+i
                    y=i-k
                else:
                    t=i+k
                    y=i-k
                if t in dict1:
                    ans.add(tuple(sorted([i,t])))
                if y in dict1:
                    ans.add(tuple(sorted([i,y])))
            return len(ans)
        else:
            count=0
            for i in range(len(nums)):
                if nums[i] in dict1:
                    dict1[nums[i]]+=1
                else:
                    dict1[nums[i]]=1
            for i in sorted(dict1):
                if dict1[i]>=2:
                    count+=1
            return count
