## Question : Minimum Cost to Convert String

### Problem Statement:
You are given two 0-indexed strings source and target, both of length n and consisting of lowercase English letters. You are also given two 0-indexed character arrays original and changed, and an integer array cost, where cost[i] represents the cost of changing the character original[i] to the character changed[i].

You start with the string source. In one operation, you can pick a character x from the string and change it to the character y at a cost of z if there exists any index j such that cost[j] == z, original[j] == x, and changed[j] == y.

Return the minimum cost to convert the string source to the string target using any number of operations. If it is impossible to convert source to target, return -1.

Note that there may exist indices i, j such that original[j] == original[i] and changed[j] == changed[i].

 
### Code (Python):
```python
class Solution:
    def minimumCost(self, source: str, target: str, original: List[str], changed: List[str], cost: List[int]) -> int:
        nodes=set(original+changed)
        mini=0
        node_list=list(nodes)
        node_index={node:idx for idx,node in enumerate(node_list)}
        n=len(nodes)
        dist=[[float('inf')]*n for i in range(n)]
        for i in range(n):
            dist[i][i]=0
        for o,c,w in zip(original,changed,cost):
            u,v=node_index[o],node_index[c]
            dist[u][v]=min(dist[u][v],w)
        for k in range(n):
            for i in range(n):
                if dist[i][k] < float('inf'):
                    for j in range(n):
                        if dist[k][j] < float('inf'):
                            dist[i][j] = min(dist[i][j],dist[i][k] + dist[k][j])
        for i in range(len(source)):
            if source[i]!=target[i]:
                if source[i] not in node_index or target[i] not in node_index:
                    return -1
                else:
                    node_s=node_index[source[i]]
                    node_t=node_index[target[i]]
                if dist[node_s][node_t]==float('inf'):
                    return -1
                mini+=dist[node_s][node_t]
        return mini
