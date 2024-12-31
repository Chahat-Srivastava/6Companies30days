## Question : Image Smoothner

### Problem Statement:
An image smoother is a filter of the size 3 x 3 that can be applied to each cell of an image by rounding down the average of the cell and the eight surrounding cells (i.e., the average of the nine cells in the blue smoother). If one or more of the surrounding cells of a cell is not present, we do not consider it in the average (i.e., the average of the four cells in the red smoother).
### Code (Python):
```python
class Solution:
    def imageSmoother(self, img: List[List[int]]) -> List[List[int]]:
        rows,columns=len(img),len(img[0])
        result=[[0]*columns for i in range(rows)]
        for i in range(rows):
            for j in range(columns):
                total_sum=0
                count=0
                for x in range(max(0,i-1),min(i+2,rows)):
                    for y in range(max(0,j-1),min(j+2,columns)):
                        total_sum+=img[x][y]
                        count+=1
                result[i][j]=total_sum//count
        return result

  
