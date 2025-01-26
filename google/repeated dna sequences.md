## Question : Repeated DNA Sequences

### Problem Statement:
The DNA sequence is composed of a series of nucleotides abbreviated as 'A', 'C', 'G', and 'T'.

For example, "ACGAATTCCG" is a DNA sequence.
When studying DNA, it is useful to identify repeated sequences within the DNA.

Given a string s that represents a DNA sequence, return all the 10-letter-long sequences (substrings) that occur more than once in a DNA molecule. You may return the answer in any order.

 
### Code (Python):
```python
class Solution:
    def findRepeatedDnaSequences(self, s: str) -> List[str]:
        n=len(s)
        count={}
        ans=[]
        for i in range(n-9):
            dna=s[i:i+10]
            if dna in count:
                count[dna]+=1
            else:
                count[dna]=1
        print(count)
        for i in sorted(count):
            if count[i]>=2:
                ans.append(i)
        return ans
        
        
