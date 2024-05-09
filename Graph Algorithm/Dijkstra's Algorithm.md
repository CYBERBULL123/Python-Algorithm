## Dijkstra's Algorithm 📐

**Definition**: Dijkstra's algorithm is a graph traversal algorithm that finds the shortest path between nodes in a weighted graph with non-negative edge weights. It starts at a selected source node and iteratively explores the closest unvisited nodes, updating the shortest distance to each node as it progresses. Dijkstra's algorithm uses a priority queue (often implemented using a min-heap) to keep track of nodes with the shortest distance from the source node, making it efficient for finding single-source shortest paths. 🚗

**Neat and Best Code**:
```python
import heapq

def dijkstra(graph, start):
    distances = {node: float('inf') for node in graph}
    distances[start] = 0
    pq = [(0, start)]

    while pq:
        current_distance, current_node = heapq.heappop(pq)

        if current_distance > distances[current_node]:
            continue

        for neighbor, weight in graph[current_node].items():
            distance = current_distance + weight
            if distance < distances[neighbor]:
                distances[neighbor] = distance
                heapq.heappush(pq, (distance, neighbor))

    return distances

# Example Usage:
graph = {
    'A': {'B': 6, 'C': 2},
    'B': {'D': 1},
    'C': {'B': 3, 'D': 5},
    'D': {}
}
start_node = 'A'
shortest_distances = dijkstra(graph, start_node)
print("Shortest distances from node", start_node + ":")
for node, distance in shortest_distances.items():
    print(f"To node {node}: {distance}")
```

**Input**: A graph represented as an adjacency list with weighted edges and a starting node from which Dijkstra's algorithm should begin.

**Output**: The shortest distances from the starting node to all other nodes in the graph.

**Implementation**:
1. Initialize a priority queue (`pq`) with the starting node and its distance from the source node.
2. While the priority queue is not empty, dequeue the node with the shortest distance from the priority queue.
3. For each neighbor of the dequeued node, calculate the distance from the source node through the dequeued node to the neighbor.
4. If the calculated distance is shorter than the current known shortest distance to the neighbor, update the shortest distance and enqueue the neighbor with its updated distance into the priority queue.
5. Repeat steps 2-4 until the priority queue is empty.

**Logic**: Dijkstra's algorithm iteratively explores the closest unvisited nodes, updating the shortest distance to each node as it progresses. It guarantees the shortest path to each node with non-negative edge weights.

**Example**: 
- **Input Graph**:
```
    A --6-- B
   /  \     /
  2    \   3
 /      \ /
C --5-- D
```
- **Output (Shortest distances from node A)**: 
  - To node A: 0
  - To node B: 6
  - To node C: 2
  - To node D: 7

**Use Case**: Dijkstra's algorithm is commonly used in network routing protocols, GPS systems, and other applications requiring finding the shortest path between nodes in a graph with non-negative edge weights.
