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

class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n
    
    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]
    
    def union(self, x, y):
        px, py = self.find(x), self.find(y)
        if px != py:
            if self.rank[px] < self.rank[py]:
                self.parent[px] = py
            elif self.rank[px] > self.rank[py]:
                self.parent[py] = px
            else:
                self.parent[py] = px
                self.rank[px] += 1
    
    def connected(self, x, y):
        return self.find(x) == self.find(y)

class Solution:
    def distanceLimitedPathsExist(self, n: int, edges: List[List[int]], queries: List[List[int]]) -> List[bool]:
        edges = sorted(edges, key=lambda x: x[2])
        ans = [False] * len(queries)
        uf = UnionFind(n)
        i = 0
        sorted_queries = sorted(enumerate(queries), key=lambda x: x[1][2])
        for q_idx, (u, v, limit) in sorted_queries:
            while i < len(edges) and edges[i][2] < limit:
                uf.union(edges[i][0], edges[i][1])
                i += 1
            ans[q_idx] = uf.connected(u, v)
        return ans

```
