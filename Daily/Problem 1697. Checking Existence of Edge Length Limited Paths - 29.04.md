# 1697. Checking Existence of Edge Length Limited Paths
## Approach:
 - Sort the queries by the limit in ascending order.
 - Sort the edges by the weight in ascending order.
 - Traverse the queries in the sorted order, and for each query, process edges with weights less than the current limit until all such edges have been processed. During processing, merge the two vertices of each edge using a Union-Find data structure.
 - Check if the two vertices of the current query are connected after all such edges have been processed. Store the result in the answer array for the current query.
 - Return the answer array.

<br></br>
## Intuition:
 - The problem requires us to check whether there exists a path between two given nodes in an undirected graph such that the weight of each edge on the path is less than or equal to a given limit.
 - We can use the Union-Find data structure to process edges in the graph in increasing order of weight and merge their endpoints if they are not already connected. This is because if two endpoints are already connected, adding the edge between them would result in a cycle and such edges cannot be included in a valid path.
 - We can then process the queries in increasing order of the limit and check if the two endpoints of each query are connected. If they are, there exists a path between them with all edges having weights less than or equal to the current limit.
 
 <br></br>
 ## Python Code:
```shell
```
