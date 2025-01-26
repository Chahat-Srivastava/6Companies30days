## Question : Count Subtree with Max Distance between Cities

### Problem Statement:
There are n cities numbered from 1 to n. You are given an array edges of size n-1, where edges[i] = [ui, vi] represents a bidirectional edge between cities ui and vi. There exists a unique path between each pair of cities. In other words, the cities form a tree.

A subtree is a subset of cities where every city is reachable from every other city in the subset, where the path between each pair passes through only the cities from the subset. Two subtrees are different if there is a city in one subtree that is not present in the other.

For each d from 1 to n-1, find the number of subtrees in which the maximum distance between any two cities in the subtree is equal to d.

Return an array of size n-1 where the dth element (1-indexed) is the number of subtrees in which the maximum distance between any two cities is equal to d.

### Code (Python):
```python
class Solution:
    def countSubgraphsForEachDiameter(self, n: int, edges: List[List[int]]) -> List[int]:
        res = [0]*(n-1)
        g = defaultdict(list)
        gs = [0]*n
        dp = [0]*(1<<n)
        for a, b in edges:
            a -= 1
            b -= 1
            g[a].append(b)
            g[b].append(a)
            gs[a] |= (1<<b)
            gs[b] |= (1<<a)
            dp[(1<<a)|(1<<b)] = 1
        dis = [[0]*n for _ in range(n)]
        def dfs(root, cur, depth, parent):
            dis[root][cur] = depth
            for nxt in g[cur]:
                if nxt == parent:
                    continue
                dfs(root, nxt, depth+1, cur)
            return

        for i in range(n):
            dfs(i,i,0,-1)
            
#         print(dis)
#         print(ees)
        
        for state in range(1<<n):
            # print(state, dp[state])
            if dp[state] > 0:
                res[dp[state]-1] += 1
                for i in range(n):
                    if dp[state | (1<<i)] == 0 and (state & gs[i]):
                        dp[state | (1<<i)] = max(dp[state], max(dis[i][j] for j in range(n) if state&(1<<j)))
        return res
