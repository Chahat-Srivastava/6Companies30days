## Question : Find Beautiful Indices in the Given Array I

### Problem Statement:
You are given a 0-indexed string s, a string a, a string b, and an integer k.

An index i is beautiful if:

0 <= i <= s.length - a.length
s[i..(i + a.length - 1)] == a
There exists an index j such that:
0 <= j <= s.length - b.length
s[j..(j + b.length - 1)] == b
|j - i| <= k
Return the array that contains beautiful indices in sorted order from smallest to largest.
### Code (Python):
```python
class Solution:
    def beautifulIndices(self, s: str, a: str, b: str, k: int) -> List[int]:
        ans=[]
        ind_a=[]
        ind_b=[]
        for i in range(len(s)-len(a)+1):
            if s[i:i+len(a)]==a:
                ind_a.append(i)
        for j in range(len(s)-len(b)+1):
            if s[j:j+len(b)]==b:
                ind_b.append(j)
        print(ind_a,ind_b)
        for i in ind_a:
            for j in ind_b:
                if abs(j-i)<=k:
                    ans.append(i)
                    break
        ans.sort()
        return ans
        
