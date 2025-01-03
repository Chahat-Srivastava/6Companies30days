## Question : Overlap Circle and Rectangle

### Problem Statement:
You are given a circle represented as (radius, xCenter, yCenter) and an axis-aligned rectangle represented as (x1, y1, x2, y2), where (x1, y1) are the coordinates of the bottom-left corner, and (x2, y2) are the coordinates of the top-right corner of the rectangle.

Return true if the circle and rectangle are overlapped otherwise return false. In other words, check if there is any point (xi, yi) that belongs to the circle and the rectangle at the same time.
### Code (Python):
```python
class Solution:
    def checkOverlap(self, radius: int, xCenter: int, yCenter: int, x1: int, y1: int, x2: int, y2: int) -> bool:
        x_close=max(x1,min(xCenter,x2))
        y_close=max(y1,min(yCenter,y2))
        distance=((x_close-xCenter)**2+(y_close-yCenter)**2)**0.5
        if distance<=radius:
            return True
        else:
            return False
                
