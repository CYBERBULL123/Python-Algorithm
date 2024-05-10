## Prim's Algorithm ⚙️

**Definition**: Prim's algorithm is a greedy algorithm that finds a minimum spanning tree (MST) for a connected, undirected graph with weighted edges. It starts with an arbitrary vertex and repeatedly adds the shortest edge that connects a vertex in the MST to a vertex outside the MST until all vertices are included in the MST. Prim's algorithm grows the MST one vertex at a time, always selecting the shortest edge that connects a vertex in the MST to a vertex outside the MST. 🌳

**Neat and Best Code**:
```python
import heapq

def prim(graph):
    mst = []
    visited = set()
    start_node = next(iter(graph))
    visited.add(start_node)
    pq = [(weight, start_node, neighbor) for neighbor, weight in graph[start_node].items()]
    heapq.heapify(pq)

    while pq:
        weight, u, v = heapq.heappop(pq)
        if v not in visited:
            visited.add(v)
            mst.append((u, v, weight))
            for neighbor, weight in graph[v].items():
                if neighbor not in visited:
                    heapq.heappush(pq, (weight, v, neighbor))

    return mst

# Example Usage:
graph = {
    'A': {'B': 2, 'D': 3},
    'B': {'A': 2, 'D': 1, 'C': 1},
    'C': {'B': 1, 'D': 1, 'E': 2},
    'D': {'A': 3, 'B': 1, 'C': 1, 'E': 1},
    'E': {'C': 2, 'D': 1}
}
minimum_spanning_tree = prim(graph)
print("Minimum Spanning Tree (MST):")
for edge in minimum_spanning_tree:
    print(edge)
```

**Input**: A graph represented as an adjacency list with weighted edges.

**Output**: The minimum spanning tree (MST) represented as a list of edges.

**Implementation**:
1. Initialize an empty MST and a set of visited vertices.
2. Choose an arbitrary vertex as the starting vertex and add it to the visited set.
3. Initialize a priority queue with the edges incident to the starting vertex.
4. While the priority queue is not empty, repeatedly select the shortest edge that connects a vertex in the MST to a vertex outside the MST.
5. Add the selected edge to the MST and mark the destination vertex as visited.
6. Add the edges incident to the newly added vertex to the priority queue if they lead to unvisited vertices.

**Logic**: Prim's algorithm grows the MST one vertex at a time by always selecting the shortest edge that connects a vertex in the MST to a vertex outside the MST, resulting in a minimum spanning tree.

**Example**: 
- **Input Graph**:
```
    A -2- B
   /   \
  3     1
 /       \
D -1- C -1- E
 \     /   2
  \   /
   \ /
    F
```
- **Output (Minimum Spanning Tree)**: 
  - (A, B, 2)
  - (B, C, 1)
  - (C, D, 1)
  - (D, E, 1)
  - (D, F, 1)

**Use Case**: Prim's algorithm is used to find the minimum spanning tree in network design, such as in designing efficient road networks or computer networks.
