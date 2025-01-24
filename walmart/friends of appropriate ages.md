## Question : Friends of Appropriate Age

### Problem Statement:
There are n persons on a social media website. You are given an integer array ages where ages[i] is the age of the ith person.

A Person x will not send a friend request to a person y (x != y) if any of the following conditions is true:

age[y] <= 0.5 * age[x] + 7
age[y] > age[x]
age[y] > 100 && age[x] < 100
Otherwise, x will send a friend request to y.

Note that if x sends a request to y, y will not necessarily send a request to x. Also, a person will not send a friend request to themself.

Return the total number of friend requests made.
### Code (Python):
```python
class Solution:
    def numFriendRequests(self, ages: List[int]) -> int:
        from collections import defaultdict
        amount_age=[0]*121
        prefixAge=[0]*121
        unique_ages=set()
        for i in ages:
            amount_age[i]+=1
            unique_ages.add(i)
        for i in range(1,len(amount_age)):
            prefixAge[i]=prefixAge[i-1]+amount_age[i]
        ans=0
        for i in unique_ages:
            l=max(i//2+7,0)
            h=i
            if l<=h:
                output=amount_age[i]*(prefixAge[h]-prefixAge[l]-1)
                ans+=max(0,output)
        return ans

        
