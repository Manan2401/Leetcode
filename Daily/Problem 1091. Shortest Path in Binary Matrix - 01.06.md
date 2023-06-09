# 1091. Shortest Path in Binary Matrix

## Approach
It uses a queue to store the grids to be processed, and initially adds the starting point to the queue. Then, take a grid out of the queue for processing, explore its adjacent grids, and add unvisited adjacent grids to the queue. This process continues until an end point is found or the queue is empty.

