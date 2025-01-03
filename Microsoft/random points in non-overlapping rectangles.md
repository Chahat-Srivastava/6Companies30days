## Question : Random Points in Non-Overlapping Rectangles

### Problem Statement:
You are given an array of non-overlapping axis-aligned rectangles rects where rects[i] = [ai, bi, xi, yi] indicates that (ai, bi) is the bottom-left corner point of the ith rectangle and (xi, yi) is the top-right corner point of the ith rectangle. Design an algorithm to pick a random integer point inside the space covered by one of the given rectangles. A point on the perimeter of a rectangle is included in the space covered by the rectangle.

Any integer point inside the space covered by one of the given rectangles should be equally likely to be returned.

Note that an integer point is a point that has integer coordinates.

Implement the Solution class:

Solution(int[][] rects) Initializes the object with the given rectangles rects.
int[] pick() Returns a random integer point [u, v] inside the space covered by one of the given rectangles.
### Code (Python):
```python
class Solution:
    import random
    def __init__(self, rects: List[List[int]]):
        self.rects=rects
        self.points=[]
        self.total=0
        for i in range(len(rects)):
            temp=rects[i]
            leftx=temp[0]
            lefty=temp[1]
            rightx=temp[2]
            righty=temp[3]
            self.total+=((rightx-leftx+1)*(righty-lefty+1))
            self.points.append(self.total)

    def pick(self) -> List[int]:
        chosen=random.randint(1,self.total)
        for i in range(len(self.rects)):
            if chosen<=self.points[i]:
                temp=self.rects[i]
                x=random.randint(temp[0],temp[2])
                y=random.randint(temp[1],temp[3])
                return [x,y]
        
        


# Your Solution object will be instantiated and called as such:
# obj = Solution(rects)
# param_1 = obj.pick()
