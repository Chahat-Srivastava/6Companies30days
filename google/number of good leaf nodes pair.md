## Question : Number of Good Leaf Nodes Pair

### Problem Statement:
You are given the root of a binary tree and an integer distance. A pair of two different leaf nodes of a binary tree is said to be good if the length of the shortest path between them is less than or equal to distance.

Return the number of good leaf node pairs in the tree.

### Code (Python):
```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, val=0, left=None, right=None):
#         self.val = val
#         self.left = left
#         self.right = right
class Solution:
    def countPairs(self, root: Optional[TreeNode], distance: int) -> int:
        self.count = 0
        MAX_DISTANCE = 10

        def dfs(node):
            if not node:
                return [0] * (MAX_DISTANCE + 1)
            
            if not node.left and not node.right:
                res = [0] * (MAX_DISTANCE + 1)
                res[1] = 1
                return res
            
            left = dfs(node.left)
            right = dfs(node.right)
            
            for i in range(1, distance + 1):
                for j in range(1, distance - i + 1):
                    self.count += left[i] * right[j]
            
            res = [0] * (MAX_DISTANCE + 1)
            for i in range(1, MAX_DISTANCE):
                res[i + 1] = left[i] + right[i]
            
            return res

        dfs(root)
        return self.count
