# 1579. Remove Max Number of Edges to Keep Graph Fully Traversable

## Approach:
 - We start by creating two separate union-find data structures for Alice and Bob. Each data structure keeps track of the root of each node, which represents the set that the node belongs to.
 - We first consider the edges that can be used by both Alice and Bob (i.e. type 3 edges). For each such edge, we perform a union operation on both union-find data structures. If the union is successful, we increment the edge count for both Alice and Bob. Otherwise, we increment the "rejected" edge count.
 - We then make copies of both union-find data structures and consider the edges that can only be used by Alice and Bob respectively (i.e. type 1 and type 2 edges). For each such edge, we perform a union operation on the corresponding union-find data structure. If the union is successful, we increment the edge count for that user. Otherwise, we increment the "rejected" edge count.
 - Finally, we check if both Alice and Bob were able to construct a spanning tree (i.e. they both used n-1 edges). If they did, we return the number of rejected edges. Otherwise, we return -1.

<br></br>
## Intuition:
 - The problem asks us to find the maximum number of edges that can be removed from the graph while still allowing both Alice and Bob to construct a spanning tree. Since a spanning tree must include all nodes in the graph, we know that there must be n-1 edges in the tree.
 - We can use the union-find data structure to keep track of which nodes are connected to each other. Initially, each node is its own root (i.e. its own set).
 - We start by considering the edges that can be used by both Alice and Bob. If we can successfully merge two nodes using a type 3 edge, we know that both Alice and Bob can use that edge to construct their respective spanning trees. Otherwise, the edge is rejected.
 - Next, we consider the edges that can only be used by Alice and Bob respectively. If a type 1 or type 2 edge can be used to connect two nodes in Alice's or Bob's respective union-find data structure, then we know that only that user can use that edge to construct their spanning tree. Otherwise, the edge is rejected.
 - Finally, we check if both Alice and Bob were able to construct a spanning tree (i.e. they both used n-1 edges). If they did, we return the number of rejected edges. Otherwise, we return -1.

<br></br>
## Python Code:
```shell
```
