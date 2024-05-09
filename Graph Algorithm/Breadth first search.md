## Breadth First Search (BFS) ➜

**Definition**: Breadth First Search is a graph traversal algorithm that explores the neighbor nodes at the present depth before moving on to nodes at the next depth level. It starts at a selected node (often called the "root") and explores all of its neighbors at the present depth level before moving on to the nodes at the next depth level. BFS uses a queue to keep track of nodes to visit, making it suitable for implementation using a queue data structure. It's used to traverse or search for nodes in a graph or tree data structure. 🌊

**Neat and Best Code**:
```python
from collections import deque

def bfs(graph, start):
    visited = set()
    queue = deque([start])
    visited.add(start)

    while queue:
        node = queue.popleft()
        print(node, end=' ')

        for neighbor in graph[node]:
            if neighbor not in visited:
                queue.append(neighbor)
                visited.add(neighbor)

# Example Usage:
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
print("Breadth First Traversal:")
bfs(graph, 'A')
```

**Input**: A graph represented as an adjacency list or adjacency matrix and a starting node from which BFS should begin.

**Output**: The nodes of the graph visited in the order of breadth-first traversal.

**Implementation**:
1. Initialize a queue with the starting node and mark it as visited.
2. While the queue is not empty, dequeue a node from the queue.
3. Print the dequeued node.
4. Enqueue all unvisited neighbor nodes of the dequeued node and mark them as visited.
5. Repeat steps 2-4 until the queue is empty.

**Logic**: BFS explores all nodes at a given depth level before moving on to nodes at the next depth level, resulting in a breadth-wise exploration of the graph structure.

**Example**: 
- **Input Graph**:
```
    A
   / \
  B   C
 / \   \
D   E   F
```
- **Output (Breadth First Traversal)**: A B C D E F

**Use Case**: BFS is commonly used in graph-related problems such as finding the shortest path, finding connected components, and solving puzzles like the sliding puzzle or the 15-puzzle.
