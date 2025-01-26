## Question : Minimum Number of Days to Disconnect Islands

### Problem Statement:
You are given an m x n binary grid grid where 1 represents land and 0 represents water. An island is a maximal 4-directionally (horizontal or vertical) connected group of 1's.

The grid is said to be connected if we have exactly one island, otherwise is said disconnected.

In one day, we are allowed to change any single land cell (1) into a water cell (0).

Return the minimum number of days to disconnect the grid.

### Code (Python):
```python

class Solution:
    def dfs(self, grid: List[List[int]], visited: List[List[bool]], i: int, j: int):
        m, n = len(grid), len(grid[0])
        if i < 0 or j < 0 or i >= m or j >= n or grid[i][j] == 0 or visited[i][j]:
            return
        visited[i][j] = True
        self.dfs(grid, visited, i+1, j)
        self.dfs(grid, visited, i-1, j)
        self.dfs(grid, visited, i, j+1)
        self.dfs(grid, visited, i, j-1)
    def countIslands(self, grid: List[List[int]]) -> int:
        m, n = len(grid), len(grid[0])
        visited = [[False] * n for _ in range(m)]
        count = 0
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1 and not visited[i][j]:
                    count += 1
                    self.dfs(grid, visited, i, j)
        return count
    def minDays(self, grid: List[List[int]]) -> int:
        if self.countIslands(grid) != 1:
            return 0
        
        m, n = len(grid), len(grid[0])
        for i in range(m):
            for j in range(n):
                if grid[i][j] == 1:
                    grid[i][j] = 0 
                    if self.countIslands(grid) != 1:
                        return 1
                    grid[i][j] = 1 
        return 2
