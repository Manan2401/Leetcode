# 839. Similar String Groups

## Intuition:
The problem can be reduced to finding connected components in an undirected graph where each node in the graph represents a string and an edge between two nodes represents that the corresponding strings are similar. If two strings are similar, we can merge their corresponding sets using the union-find data structure. At the end, the number of disjoint sets in the union-find data structure represents the number of connected components in the graph, which gives us the number of groups of similar strings.

To check if two strings are similar, we can simply compare them character by character and count the number of differences. If the number of differences is greater than 2, then we can say that the two strings are not similar. Otherwise, we can say that they are similar and can be merged into the same set.

<br></br>
## Approach:
The problem asks us to group strings that are similar. Two strings are considered similar if they can be transformed into each other by swapping at most two letters. To solve this problem, we can use the union-find algorithm. We can first iterate over all pairs of strings in the input array and check if they are similar or not. If they are similar, we union their corresponding sets in the union-find data structure. Finally, we return the number of disjoint sets in the union-find data structure.

To check if two strings are similar, we can iterate over both strings and check if the number of differences between the characters in the two strings is less than or equal to 2.

<br></br>
## Python Code:
```shell
class UnionFind:
    def __init__(self, n):
        self.parent = list(range(n))
        self.rank = [0] * n
        self.count = n

    def find(self, x):
        if self.parent[x] != x:
            self.parent[x] = self.find(self.parent[x])
        return self.parent[x]

    def union(self, x, y):
        root_x = self.find(x)
        root_y = self.find(y)

        if root_x == root_y:
            return False

        if self.rank[root_x] < self.rank[root_y]:
            root_x, root_y = root_y, root_x

        self.parent[root_y] = root_x

        if self.rank[root_x] == self.rank[root_y]:
            self.rank[root_x] += 1

        self.count -= 1

        return True

class Solution:
    def numSimilarGroups(self, strs: List[str]) -> int:
        def is_similar(s1, s2):
            if s1 == s2:
                return True

            diff = 0
            for c1, c2 in zip(s1, s2):
                if c1 != c2:
                    diff += 1
                    if diff > 2:
                        return False

            return diff == 2

        n = len(strs)
        uf = UnionFind(n)

        for i in range(n):
            for j in range(i + 1, n):
                if is_similar(strs[i], strs[j]):
                    uf.union(i, j)

        return uf.count

```
