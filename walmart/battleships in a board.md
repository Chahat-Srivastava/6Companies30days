## Question : Battleships in a Board

### Problem Statement:
Given an m x n matrix board where each cell is a battleship 'X' or empty '.', return the number of the battleships on board.

Battleships can only be placed horizontally or vertically on board. In other words, they can only be made of the shape 1 x k (1 row, k columns) or k x 1 (k rows, 1 column), where k can be of any size. At least one horizontal or vertical cell separates between two battleships (i.e., there are no adjacent battleships).

### Code (Python):
```python
class Solution:
    def countBattleships(self, board: List[List[str]]) -> int:
        count=0
        for i,row in enumerate(board):
            for j,cell in enumerate(row):
                if cell=="X":
                    if (i==0 or board[i-1][j]==".") and (j==0 or board[i][j-1]=="."):
                        count+=1
        return count
        
