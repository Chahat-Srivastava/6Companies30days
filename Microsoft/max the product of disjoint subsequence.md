## Question : Maximum Product of Disjoint Palindrome Subsequence

### Problem Statement:
Given a string s, find two disjoint palindromic subsequences of s such that the product of their lengths is maximized. The two subsequences are disjoint if they do not both pick a character at the same index.

Return the maximum possible product of the lengths of the two palindromic subsequences.

A subsequence is a string that can be derived from another string by deleting some or no characters without changing the order of the remaining characters. A string is palindromic if it reads the same forward and backward.
### Code (Python):
```python
class Solution:
    def maxProduct(self, s: str) -> int:
        n,par=len(s),{}
        for mask in range(1,1<<n):
            subseq=""
            for i in range(n):
                if mask & (1<<i):
                    subseq+=s[i]
            if subseq==subseq[::-1]:
                par[mask]=len(subseq)
        res=0
        for m1 in par:
            for m2 in par:
                if m1&m2==0:
                    res=max(res,par[m1]*par[m2])
        return res

        
