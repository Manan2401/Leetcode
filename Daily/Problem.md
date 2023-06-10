# 1
## Python Code
```shell
class Solution:
    def countNegatives(self, grid: List[List[int]]) -> int:
        neg=0
        for i in range(len(grid)):
            for j in range(len(grid[0])-1, -1, -1):
                if grid[i][j]<0:
                    neg+=1
                else:
                    break
        return neg
```
