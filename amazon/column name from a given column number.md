## Question : Excel Sheet Column Title

### Problem Statement:
Given an integer columnNumber, return its corresponding column title as it appears in an Excel sheet.

For example:

A -> 1
B -> 2
C -> 3
...
Z -> 26
AA -> 27
AB -> 28 
...
### Code (Python):
```python
class Solution:
    def convertToTitle(self, columnNumber: int) -> str:
        result=[]
        while columnNumber>0:
            columnNumber-=1
            result.append(chr(columnNumber%26+ord('A')))
            columnNumber//=26
        return ''.join(result[::-1])
