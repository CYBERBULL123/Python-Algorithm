## Depth First Search (DFS) 🕳️

**Definition**: Depth First Search is a graph traversal algorithm that explores as far as possible along each branch before backtracking. It starts at a selected node (often called the "root") and explores as far as possible along each branch before backtracking. DFS uses a stack to keep track of nodes to visit, making it suitable for implementation using recursion or an explicit stack data structure. It's used to traverse or search for nodes in a graph or tree data structure. 🌲

**Neat and Best Code (Recursive DFS)**:
```python
def dfs(graph, start, visited=None):
    if visited is None:
        visited = set()
    visited.add(start)
    print(start, end=' ')

    for neighbor in graph[start]:
        if neighbor not in visited:
            dfs(graph, neighbor, visited)

# Example Usage:
graph = {
    'A': ['B', 'C'],
    'B': ['D', 'E'],
    'C': ['F'],
    'D': [],
    'E': ['F'],
    'F': []
}
print("Depth First Traversal:")
dfs(graph, 'A')
```

**Input**: A graph represented as an adjacency list or adjacency matrix and a starting node from which DFS should begin.

**Output**: The nodes of the graph visited in the order of depth-first traversal.

**Implementation**:
1. Mark the starting node as visited and print it.
2. For each neighbor of the starting node that has not been visited, recursively call DFS on that neighbor.
3. Repeat step 2 for all unvisited neighbors of the current node until all nodes reachable from the starting node have been visited.

**Logic**: DFS explores as far as possible along each branch before backtracking, which means it traverses deeper into the graph structure before exploring other branches.

**Example**: 
- **Input Graph**:
```
    A
   / \
  B   C
 / \   \
D   E   F
```
- **Output (Depth First Traversal)**: A B D E F C

**Use Case**: DFS is commonly used in graph-related problems such as finding connected components, cycle detection, topological sorting, and solving maze-like puzzles.
