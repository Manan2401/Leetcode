# 1232. Check If It Is a Straight Line

## Approach:
To determine if a set of points lies on a straight line, we can check if the slopes between any two consecutive points are equal. If all the slopes are equal, then the points lie on a straight line; otherwise, they do not.

## Python Code
```shell
class Solution:
    def checkStraightLine(self, coordinates):
        x0, y0 = coordinates[0]
        x1, y1 = coordinates[1]

        for i in range(2, len(coordinates)):
            x, y = coordinates[i]
            if (x - x0) * (y1 - y0) != (y - y0) * (x1 - x0):
                return False

        return True
```
