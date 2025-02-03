## Question : Run Length Encoding

### Problem Statement:
Given a string s, Your task is to complete the function encode that returns the run length encoded string for the given string.
eg if the input string is “wwwwaaadexxxxxx”, then the function should return “w4a3d1e1x6″.
You are required to complete the function encode that takes only one argument the string which is to be encoded and returns the encoded string.

### Code (Python):
```python
class Solution:
    def encode(self, s : str) -> str:
        ans=""
        count=1
        for i in range(1,len(s)):
            if s[i-1]==s[i]:
                count+=1
            else:
                ans+=s[i-1]+str(count)
                count=1
        ans+=s[i]+str(count)
        return ans
