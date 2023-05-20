# 399. Evaluate Division
## Approach:
The problem can be solved using graph traversal, specifically breadth-first search (BFS). We can represent the given equations as a graph, where each variable is a node, and the values represent the edges between the nodes. The division result between two variables can be found by traversing from the dividend node to the divisor node and multiplying the edge values encountered along the path.

 - Build the graph: Iterate through the given equations and values, and construct an adjacency map that represents the graph. For each equation (a / b = k), add edges (a, b) and (b, a) to the graph with edge values k and 1/k, respectively.

 - Evaluate queries: For each query (x, y), perform a BFS starting from node x and searching for node y. During the BFS traversal, keep track of the product of the edge values encountered. If y is reached, return the product as the division result. If y is not reached or either x or y is not present in the graph, return -1.

<br></br>

## Python Code
```shell
from collections import defaultdict, deque

class Solution:
    def calcEquation(self, equations, values, queries):
        graph = self.buildGraph(equations, values)
        results = []
        
        for dividend, divisor in queries:
            if dividend not in graph or divisor not in graph:
                results.append(-1.0)
            else:
                result = self.bfs(dividend, divisor, graph)
                results.append(result)
        
        return results
    
    def buildGraph(self, equations, values):
        graph = defaultdict(dict)
        
        for (dividend, divisor), value in zip(equations, values):
            graph[dividend][divisor] = value
            graph[divisor][dividend] = 1.0 / value
        
        return graph
    
    def bfs(self, start, end, graph):
        queue = deque([(start, 1.0)])
        visited = set()
        
        while queue:
            node, value = queue.popleft()
            
            if node == end:
                return value
            
            visited.add(node)
            
            for neighbor, weight in graph[node].items():
                if neighbor not in visited:
                    queue.append((neighbor, value * weight))
        
        return -1.0
```
