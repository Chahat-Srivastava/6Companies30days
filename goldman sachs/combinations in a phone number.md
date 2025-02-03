## Question : Combinations in a Phone Number

### Problem Statement:
Given a string containing digits from 2-9 inclusive, return all possible letter combinations that the number could represent. Return the answer in any order.

A mapping of digits to letters (just like on the telephone buttons) is given below. Note that 1 does not map to any letters.

### Code (Python):
```python
class Solution:
    def letterCombinations(self, digits: str) -> List[str]:
        if not digits:
            return []
        dict1={'2':"abc",'3':"def",'4':"ghi",'5':"jkl",'6':"mno",'7':"pqrs",'8':"tuv",'9':"wxyz"}
        def backtrack(i,comb):
            if i==len(digits):
                res.append(comb[:])
                return
            for l in dict1[digits[i]]:
                backtrack(i+1,comb+l)
        res=[]
        backtrack(0,"")
        return res
