## Question : Following a Number Pattern

### Problem Statement:
Given a pattern containing only I's and D's. I for increasing and D for decreasing. Devise an algorithm to print the minimum number following that pattern. Digits from 1-9 and digits can't repeat.

### Code (Python):
```python
class Solution:
    def printMinNumberForPattern(ob,S):
        result=[]
        s=[]
        num=1
        for c in S:
            s.append(str(num))
            num+=1
            if c=="I":
                result+=s[::-1]
                s=[]
        s.append(str(num))
        result+=s[::-1]
        return int(''.join(result))
