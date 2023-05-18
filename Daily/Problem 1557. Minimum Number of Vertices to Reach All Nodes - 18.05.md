# 1557. Minimum Number of Vertices to Reach All Nodes

## Approach:
 - Create a set all_nodes containing all the node values from 0 to n-1. This set represents all the nodes in the graph.
 - Create a set destination_nodes to store the destination nodes from the edges list. Iterate through each edge and add the destination node to the set.
 - Compute the set difference between all_nodes and destination_nodes to obtain the set of source nodes. These are the nodes that do not have any incoming edges and can reach all other nodes directly or indirectly.
 - Convert the set of source nodes to a list and return the result.

<br></br>
## Python Code:
```shell
class Solution:
    def findSmallestSetOfVertices(self, n, edges):
        all_nodes = set(range(n))
        destination_nodes = set(destination for _, destination in edges)
        source_nodes = all_nodes - destination_nodes
        return list(source_nodes)
```
