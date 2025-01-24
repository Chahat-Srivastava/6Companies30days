## Question : Sort characters by Frequency

### Problem Statement:
Given a string s, sort it in decreasing order based on the frequency of the characters. The frequency of a character is the number of times it appears in the string.

Return the sorted string. If there are multiple answers, return any of them.

Example 1:

Input: s = "tree"
Output: "eert"
Explanation: 'e' appears twice while 'r' and 't' both appear once.
So 'e' must appear before both 'r' and 't'. Therefore "eetr" is also a valid answer.
### Code (Python):
```python
class Solution:
    def frequencySort(self, s: str) -> str:
        dict1={}
        ans=""
        for i in range(len(s)):
            if s[i] in dict1:
                dict1[s[i]]+=1
            else:
                dict1[s[i]]=1
        dict2=dict(sorted(dict1.items(),key=lambda item:item[1],reverse=True))
        for i in dict2:
            ans+=dict2[i]*i
        return ans
        
