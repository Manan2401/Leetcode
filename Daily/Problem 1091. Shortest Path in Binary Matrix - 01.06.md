# 1091. Shortest Path in Binary Matrix

## Approach
It uses a queue to store the grids to be processed, and initially adds the starting point to the queue. Then, take a grid out of the queue for processing, explore its adjacent grids, and add unvisited adjacent grids to the queue. This process continues until an end point is found or the queue is empty.

<br></br>
## Python Code
```shell
class Solution:
    def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
        n = len(grid)

        # Check if the start/end cell is blocked.
        if grid[0][0] != 0 or grid[n-1][n-1] != 0:
            return -1

        # Create a queue for BFS and enqueue the start cell
        queue = deque([(0, 0, 1)])  #(row, col, path_length)

        # Offset in 8 directions
        directions = [(-1, -1), (-1, 0), (-1, 1), (0, -1), (0, 1), (1, -1), (1, 0), (1, 1)]
        
        # Execute BFS
        while queue:

            row, col, path_len = queue.popleft()
            
            # Check if the goal has been reached.
            if row == n-1 and col == n-1:
                return path_len

            # Explore adjacent grids.
            for i, j in directions:
                neighbour_row = i + row
                neighbour_col = j + col

                # Check if the adjacent grid is within the grid range and has not been visited
                if 0 <= neighbour_row < n and 0 <= neighbour_col < n and grid[neighbour_row][neighbour_col] == 0:
                    # Mark adjacent cells as visited (set to 1)
                    grid[neighbour_row][neighbour_col] = 1
                    queue.append((neighbour_row, neighbour_col, path_len + 1))

        # No clear path found
        return -1
```
