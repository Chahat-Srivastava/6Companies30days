## Question : Assign Cookies

### Problem Statement:
Assume you are an awesome parent and want to give your children some cookies. But, you should give each child at most one cookie.

Each child i has a greed factor g[i], which is the minimum size of a cookie that the child will be content with; and each cookie j has a size s[j]. If s[j] >= g[i], we can assign the cookie j to the child i, and the child i will be content. Your goal is to maximize the number of your content children and output the maximum number.
### Code (Python):
```python
class Solution:
    def findContentChildren(self, g: List[int], s: List[int]) -> int:
        i,j=0,0
        s.sort()
        g.sort()
        res=[]
        while i<len(g) and j<len(s):
            if g[i]==s[j]:
                res.append(g[i])
                i=i+1
                j=j+1
            elif g[i]>s[j]:
                j=j+1
            else:
                res.append(g[i])
                j=j+1
                i=i+1
        return len(res)
