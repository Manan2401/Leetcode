# 934. Shortest Bridge
## Approach:
 - Perform a depth-first search (DFS) to find the first island in the grid. Mark the visited cells as you traverse through the island.
 - Start a breadth-first search (BFS) from the visited cells of the first island. Keep expanding to neighboring cells until you find the second island or exhaust all possible cells.
 - During the BFS, maintain the level (distance) from the first island. Return the level when you encounter the second island.
 - If no second island is found, return -1 to indicate that no bridge exists between the two islands.
