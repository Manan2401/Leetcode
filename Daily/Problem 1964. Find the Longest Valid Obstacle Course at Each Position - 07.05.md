# 1964. Find the Longest Valid Obstacle Course at Each Position

## Approach:
The given problem can be solved using the dynamic programming approach. We can maintain an array lis that stores the longest increasing subsequence encountered so far. For each obstacle, we find the position where it should be inserted into the lis array using binary search, and update the lis array accordingly. Finally, we append the length of the lis array to the result array.

<br></br>
## Python Code:
```shell
import bisect

class Solution:
    def longestObstacleCourseAtEachPosition(self, obstacles: List[int]) -> List[int]:
        lis = []
        result = []
        for obstacle in obstacles:
            idx = bisect.bisect_right(lis, obstacle)
            if idx == len(lis):
                lis.append(obstacle)
            else:
                lis[idx] = obstacle
            result.append(idx+1)
        return result
```
