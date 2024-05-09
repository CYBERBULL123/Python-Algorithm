## Kruskal's Algorithm ⏲

**Definition**: Kruskal's algorithm is a greedy algorithm that finds a minimum spanning tree (MST) for a connected, undirected graph with weighted edges. It starts with an empty graph and adds the shortest edge that does not form a cycle in the graph until all vertices are connected. Kruskal's algorithm is particularly efficient for sparse graphs and is based on the principle of finding the minimum weight edge that connects two disjoint sets of vertices. 🌉

**Neat and Best Code**:
```python
class DisjointSet:
    def __init__(self, n):
        self.parent = [i for i in range(n)]
        self.rank = [0] * n

    def find(self, u):
        if self.parent[u] != u:
            self.parent[u] = self.find(self.parent[u])
        return self.parent[u]

    def union(self, u, v):
        pu, pv = self.find(u), self.find(v)
        if pu == pv:
            return False
        if self.rank[pu] < self.rank[pv]:
            self.parent[pu] = pv
        elif self.rank[pu] > self.rank[pv]:
            self.parent[pv] = pu
        else:
            self.parent[pv] = pu
            self.rank[pu] += 1
        return True

def kruskal(graph):
    edges = [(weight, u, v) for u, adj in graph.items() for v, weight in adj.items()]
    edges.sort()
    mst = []
    ds = DisjointSet(len(graph))

    for weight, u, v in edges:
        if ds.union(u, v):
            mst.append((u, v, weight))

    return mst

# Example Usage:
graph = {
    'A': {'B': 7, 'D': 5},
    'B': {'A': 7, 'D': 9, 'C': 8, 'E': 7},
    'C': {'B': 8, 'E': 5},
    'D': {'A': 5, 'B': 9, 'E': 15, 'F': 6},
    'E': {'B': 7, 'C': 5, 'D': 15, 'F': 8, 'G': 9},
    'F': {'D': 6, 'E': 8, 'G': 11},
    'G': {'E': 9, 'F': 11}
}
minimum_spanning_tree = kruskal(graph)
print("Minimum Spanning Tree (MST):")
for edge in minimum_spanning_tree:
    print(edge)
```

**Input**: A graph represented as an adjacency list with weighted edges.

**Output**: The minimum spanning tree (MST) represented as a list of edges.

**Implementation**:
1. Sort all edges of the graph by weight in non-decreasing order.
2. Initialize an empty MST and a disjoint set data structure.
3. Iterate through sorted edges, adding each edge to the MST if it does not form a cycle in the current MST.
4. Union the two sets of vertices connected by the edge.

**Logic**: Kruskal's algorithm greedily selects the shortest edge that does not form a cycle, effectively growing a forest of trees into a single spanning tree (MST).

**Example**: 
- **Input Graph**:
```
    A -7- B
   / \    \
  5   \   8
 /     \   \
D -9- C -5- E
 \     /  15/ 7\ 9
  6   /   /   \   \
   \ /   8     6   G
    F -11- E -11-/
```
- **Output (Minimum Spanning Tree)**: 
  - (A, D, 5)
  - (C, E, 5)
  - (D, F, 6)
  - (A, B, 7)
  - (B, E, 7)
  - (E, G, 9)

**Use Case**: Kruskal's algorithm is used to find the minimum spanning tree in network design, such as in designing efficient road networks or computer networks.
