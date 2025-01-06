## Question : Which among them form a perfect Soduko

### Problem Statement:
Determine if a 9 x 9 Sudoku board is valid. Only the filled cells need to be validated according to the following rules:

Each row must contain the digits 1-9 without repetition.
Each column must contain the digits 1-9 without repetition.
Each of the nine 3 x 3 sub-boxes of the grid must contain the digits 1-9 without repetition.
Note:

A Sudoku board (partially filled) could be valid but is not necessarily solvable.
Only the filled cells need to be validated according to the mentioned rules.
### Code (Python):
```python
class Solution:
    def isValid(self,row,col,k,board):
        for i in range(len(board)):
            if board[row][i]==k:
                return False
            if board[i][col]==k:
                return False
            if board[3*(row//3)+i//3][3*(col//3)+i%3]==k:
                return False
        return True
    def isValidSudoku(self, board: List[List[str]]) -> bool:
        for i in range(len(board)):
            for j in range(len(board[0])):
                if board[i][j]!=".":
                    k=board[i][j]
                    board[i][j]="."
                    if self.isValid(i,j,k,board)==False:
                        print(i,j,board[i][j])
                        return False
                    board[i][j]=k
        return True
