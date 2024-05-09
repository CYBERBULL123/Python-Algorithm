## Bellman-Ford Algorithm 📊

**Definition**: Bellman-Ford algorithm is a graph traversal algorithm that finds the shortest path from a source node to all other nodes in a weighted graph, even in the presence of negative edge weights, as long as the graph does not contain negative cycles reachable from the source node. It iterates over all edges in the graph and relaxes them iteratively, updating the shortest distances until no further improvements can be made. Bellman-Ford algorithm can detect negative cycles and is slower than Dijkstra's algorithm but more versatile. 🛤️

**Neat and Best Code**:
```python
def bellman_ford(graph, start):
    # Step 1: Initialize distances
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    
    # Step 2: Relax edges repeatedly
    for _ in range(len(graph) - 1):
        for node in graph:
            for neighbor, weight in graph[node].items():
                if distances[node] + weight < distances[neighbor]:
                    distances[neighbor] = distances[node] + weight
    
    # Step 3: Check for negative cycles
    for node in graph:
        for neighbor, weight in graph[node].items():
            if distances[node] + weight < distances[neighbor]:
                raise ValueError("Graph contains negative cycle")
    
    return distances

# Example Usage:
graph = {
    'A': {'B': -1, 'C': 4},
    'B': {'C': 3, 'D': 2, 'E': 2},
    'C': {},
    'D': {'B': 1, 'C': 5},
    'E': {'D': -3}
}
start_node = 'A'
shortest_distances = bellman_ford(graph, start_node)
print("Shortest distances from node", start_node + ":")
for node, distance in shortest_distances.items():
    print(f"To node {node}: {distance}")
```

**Input**: A graph represented as an adjacency list with weighted edges and a starting node from which the Bellman-Ford algorithm should begin.

**Output**: The shortest distances from the starting node to all other nodes in the graph.

**Implementation**:
1. Initialize distances to all nodes as infinity except for the starting node which is set to 0.
2. Repeat relaxation step (updating distances) for `|V| - 1` times where `|V|` is the number of vertices in the graph.
3. Check for negative cycles by iterating over all edges in the graph and relaxing them again. If any further improvements can be made after the `|V| - 1` iterations, it indicates the presence of a negative cycle.
4. Return the distances to all nodes.

**Logic**: Bellman-Ford algorithm iteratively relaxes edges in the graph, updating the shortest distances to each node until no further improvements can be made or until negative cycles are detected.

**Example**: 
- **Input Graph**:
```
    A --(-1)-- B
    |  \        \
    |    \       \ 2
    |      \     V
    |        -> E
    |      /     ^
    |    /       / -3
    V  /        /
    C --(4)--- D
```
- **Output (Shortest distances from node A)**: 
  - To node A: 0
  - To node B: -1
  - To node C: 2
  - To node D: -2
  - To node E: 1

**Use Case**: Bellman-Ford algorithm is used in scenarios where the graph contains negative edge weights or when negative cycles need to be detected, such as in network routing protocols and distributed systems.
