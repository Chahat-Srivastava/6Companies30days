## Question : Russian Dolls Envelopes

### Problem Statement:
You are given a 2D array of integers envelopes where envelopes[i] = [wi, hi] represents the width and the height of an envelope.

One envelope can fit into another if and only if both the width and height of one envelope are greater than the other envelope's width and height.

Return the maximum number of envelopes you can Russian doll (i.e., put one inside the other).

Note: You cannot rotate an envelope.
### Code (Python):
```python
class Solution:
    def maxEnvelopes(self, envelopes: List[List[int]]) -> int:
        envelopes.sort(key=lambda x:(x[0],-x[1]))
        output=[]
        for i,h in envelopes:
            l,r=0,len(output)-1
            while l<=r:
                mid=(l+r)>>1
                if output[mid]>=h:
                    r=mid-1
                else:
                    l=mid+1
            idx=l
            if idx==len(output):
                output.append(h)
            else:
                output[idx]=h
        return len(output)
        
