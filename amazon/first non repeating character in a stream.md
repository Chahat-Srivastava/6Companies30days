## Question : First Non Repeating Character in a Stream

### Problem Statement:
Given a string s, find the first non-repeating character in it and return its index. If it does not exist, return -1.
### Code (Python):
```python
class Solution:
    def firstUniqChar(self, s: str) -> int:
        from collections import defaultdict
        dict1=defaultdict(lambda:[])
        for i in range(len(s)):
            dict1[s[i]].append(i)
        print(dict1)
        index=float('inf')
        for i in sorted(dict1):
            if len(dict1[i])==1:
                index=min(index,min(dict1[i]))
        if index==float('inf'):
            return -1
        else:
            return index
