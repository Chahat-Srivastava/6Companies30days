## Question : Find the City with Smallest Number of Neighbors at a Threshold Distance

### Problem Statement:
There are n cities numbered from 0 to n-1. Given the array edges where edges[i] = [fromi, toi, weighti] represents a bidirectional and weighted edge between cities fromi and toi, and given the integer distanceThreshold.

Return the city with the smallest number of cities that are reachable through some path and whose distance is at most distanceThreshold, If there are multiple such cities, return the city with the greatest number.

Notice that the distance of a path connecting cities i and j is equal to the sum of the edges' weights along that path.
### Code (Python):
```python
class Solution:
    def findTheCity(self, n: int, edges: List[List[int]], distanceThreshold: int) -> int:
        graph=[[float('inf')]*n for i in range(n)]
        for i in range(n):
            graph[i][i]=0
        for temp in edges:
            f,t,cost=temp
            graph[f][t]=min(graph[f][t],cost)
            graph[t][f]=min(graph[t][f],cost)
        print(graph)
        for k in range(n):
            for i in range(n):
                if graph[i][k]<float('inf'):
                    for j in range(n):
                        if graph[k][j]<float('inf'):
                            graph[i][j]=min(graph[i][j],graph[i][k]+graph[k][j])
        print(graph)
        res=None
        mini=n
        for i in range(n):
            count=0
            for j in range(n):
                if graph[i][j]<=distanceThreshold:
                    count+=1
            if count<=mini:
                mini=count
                res=i
        return res


        
