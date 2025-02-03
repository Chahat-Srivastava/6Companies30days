## Question : Map of Highest Peak

### Problem Statement:
You are given an integer matrix isWater of size m x n that represents a map of land and water cells.

If isWater[i][j] == 0, cell (i, j) is a land cell.
If isWater[i][j] == 1, cell (i, j) is a water cell.
You must assign each cell a height in a way that follows these rules:

The height of each cell must be non-negative.
If the cell is a water cell, its height must be 0.
Any two adjacent cells must have an absolute height difference of at most 1. A cell is adjacent to another cell if the former is directly north, east, south, or west of the latter (i.e., their sides are touching).
Find an assignment of heights such that the maximum height in the matrix is maximized.

Return an integer matrix height of size m x n where height[i][j] is cell (i, j)'s height. If there are multiple solutions, return any of them.

### Code (Python):
```python
class Solution:
    def highestPeak(self, isWater: List[List[int]]) -> List[List[int]]:
        stack=[]
        visited=set()
        dp=[[0]*len(isWater[0]) for i in range(len(isWater))]
        for i in range(len(isWater)):
            for j in range(len(isWater[0])):
                if isWater[i][j]==1:
                    stack.append((i,j,0))
                    visited.add((i,j))
        while stack:
            x,y,d=stack.pop(0)
            dp[x][y]=d
            for n1,n2 in [(x+1,y),(x-1,y),(x,y+1),(x,y-1)]:
                if n1>=0 and n1<len(isWater) and n2>=0 and n2<len(isWater[0]) and (n1,n2) not in visited:
                    stack.append((n1,n2,d+1))
                    visited.add((n1,n2))
        return dp

        
