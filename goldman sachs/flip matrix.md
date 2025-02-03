## Question : Flip Matrix

### Problem Statement:
There is an m x n binary grid matrix with all the values set 0 initially. Design an algorithm to randomly pick an index (i, j) where matrix[i][j] == 0 and flips it to 1. All the indices (i, j) where matrix[i][j] == 0 should be equally likely to be returned.

Optimize your algorithm to minimize the number of calls made to the built-in random function of your language and optimize the time and space complexity.

Implement the Solution class:

Solution(int m, int n) Initializes the object with the size of the binary matrix m and n.
int[] flip() Returns a random index [i, j] of the matrix where matrix[i][j] == 0 and flips it to 1.
void reset() Resets all the values of the matrix to be 0.

### Code (Python):
```python
class Solution:

    def __init__(self, m: int, n: int):
        self.m=m
        self.n=n
        self.total=m*n
        self.used=set()

    def flip(self) -> List[int]:
        r=random.randint(0,self.total-1)
        while r in self.used:
            r=random.randint(0,self.total-1)
        self.used.add(r)
        return [r//self.n,r%self.n]

    def reset(self) -> None:
        self.used=set()
        


# Your Solution object will be instantiated and called as such:
# obj = Solution(m, n)
# param_1 = obj.flip()
# obj.reset()
