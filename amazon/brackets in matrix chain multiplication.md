## Question : Brackets in Matrix Chain Multiplication

### Problem Statement:
Given an array arr[] of length n used to denote the dimensions of a series of matrices such that the dimension of i'th matrix is arr[i] * arr[i+1]. There are a total of n-1 matrices. Find the most efficient way to multiply these matrices together. 
As in MCM, you were returning the most effective count but this time return the string which is formed of A - Z (only Uppercase) denoting matrices & Brackets( "(" ")" ) denoting multiplication symbols. For example, if n =11, the matrixes can be denoted as A - K as n<=26 & brackets as multiplication symbols.

NOTE:

Each multiplication is denoted by putting open & closed brackets to the matrices multiplied & also, please note that the order of matrix multiplication matters, as matrix multiplication is non-commutative A*B != B*A
As there can be multiple possible answers, the console would print "true" for the correct string and "false" for the incorrect string. You need to only return a string that performs a minimum number of multiplications.
### Code (Python):
```python
class Solution:
    def help1(self,i,j,brackets):
        if i==j:
            a=chr(ord('A')+i-1)
            temp=""
            temp+=a
            return temp
        return '('+self.help1(i,brackets[i][j],brackets)+self.help1(brackets[i][j]+1,j,brackets)+')'
    def matrixChainOrder(self, arr):
        n=len(arr)
        dp=[[float('inf')]*n for i in range(n)]
        brackets=[[0]*n for i in range(n)]
        for i in range(n):
            dp[i][i]=0
        for i in range(2,n):
            for j in range(1,n-i+1):
                end=j+i-1
                for k in range(j,end):
                    total = dp[j][k]+dp[k+1][end]+arr[j-1]*arr[k]*arr[end]
                    if total<dp[j][end]:
                        dp[j][end]=total
                        brackets[j][end]=k
        return self.help1(1,n-1,brackets)
