## Question : Nuts and Bolts Problem

### Problem Statement:
Given a set of n nuts & bolts. There is a one-on-one mapping between nuts and bolts. You have to Match nuts and bolts efficiently. Comparison of a nut to another nut or a bolt to another bolt is not allowed. It means the nut can only be compared with the bolt and the bolt can only be compared with the nut to see which one is bigger/smaller.
The elements should follow the following order: { !,#,$,%,&,*,?,@,^ }

Note: Make all the required changes directly in the given arrays, output will be handled by the driver code.
### Code (Python):
```python
class Solution:

	def matchPairs(self, n, nuts, bolts):
		order=['!','#','$','%','&','*','?','@','^']
		pos=0
		for i in range(9):
		    for j in range(n):
		        if order[i]==bolts[j]:
		            bolts[j],bolts[pos]=bolts[pos],bolts[j]
		            nuts[pos]=bolts[pos]
		            pos+=1
