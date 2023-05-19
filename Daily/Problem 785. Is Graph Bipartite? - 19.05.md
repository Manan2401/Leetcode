# 785. Is Graph Bipartite?
## Appraoch
We can solve this problem using a depth-first search (DFS) approach. The idea is to assign colors to the nodes of the graph such that adjacent nodes have different colors. We start by initializing an array to keep track of the colors assigned to each node. Then, for each unvisited node in the graph, we perform a DFS to explore its neighbors. During the DFS, we assign alternating colors to the current node and its neighbors. If we encounter a neighbor that already has a color assigned and it is the same as the current node's color, then the graph is not bipartite. If we successfully color all the nodes without conflicts, the graph is bipartite.

<br></br>
