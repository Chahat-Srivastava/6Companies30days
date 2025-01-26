## Question : Stone Games IV

### Problem Statement:
Alice and Bob take turns playing a game, with Alice starting first.

There are n stones in a pile. On each player's turn, they can remove a stone from the pile and receive points based on the stone's value. Alice and Bob may value the stones differently.

You are given two integer arrays of length n, aliceValues and bobValues. Each aliceValues[i] and bobValues[i] represents how Alice and Bob, respectively, value the ith stone.

The winner is the person with the most points after all the stones are chosen. If both players have the same amount of points, the game results in a draw. Both players will play optimally. Both players know the other's values.

Determine the result of the game, and:

If Alice wins, return 1.
If Bob wins, return -1.
If the game results in a draw, return 0.
 
### Code (Python):
```python
class Solution:
    def stoneGameVI(self, aliceValues: List[int], bobValues: List[int]) -> int:
        temp=[(aliceValues[i]+bobValues[i],aliceValues[i],bobValues[i]) for i in range(len(aliceValues))]
        temp.sort(reverse=True)
        alice=0
        bob=sum(bobValues)
        for i in range(0,len(aliceValues),2):
            alice+=temp[i][1]
            bob-=temp[i][2]
        if alice>bob:
            return 1
        elif bob>alice:
            return -1
        return 0
        
        
