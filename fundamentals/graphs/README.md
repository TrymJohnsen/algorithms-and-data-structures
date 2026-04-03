
# Graphs

## Algorithm Overview

| Algorithm | Category | Time Complexity | Space | Use case |
|---|---|---|---|---|
| **BFS** | Traversal | O(V + E) | O(V) | Shortest path (unweighted), level-order |
| **DFS** | Traversal | O(V + E) | O(V) | Cycle detection, topological sort, SCC |
| **Kosarajus** | SCC | O(V + E) | O(V + E) | Find strongly connected components |
| **Kruskal** | MST | O(E log E) | O(V) | Minimum spanning tree |
| **Ford-Fulkerson** | Flow | O(E · |f|) | O(V + E) | Max flow / min cut |
| **Dijkstra** | SSSP | O((V + E) log V) | O(V) | Shortest path from one source (non-negative weights) |
| **Bellman-Ford** | SSSP | O(V · E) | O(V) | Shortest path, handles negative weights |
| **DAG Shortest Path** | SSSP | O(V + E) | O(V) | Shortest path in directed acyclic graphs |
| **Floyd-Warshall** | APSP | O(V³) | O(V²) | All-pairs shortest paths |

<br>

## Topological Sort

Creates an order of nodes so that all arrows (edges) is pointing forward

- Topological sorting is used at direct, acyclic graphs (DAGs)
- Typical use: dependencies between tasks, planning, course-order

Topological sorting is a spesific problem that can be solved with the help of DFS or BFS

### DFS

Depth-First-Search based methods uses Finish-time to find the order.
We sort the nodes in decreasing order after finishtime. 
- A node is finished when all its descendants is finished
- Explores all the children and granchildren of a node 
- Uses a LIFO-queue (Last in - first out), a stack more spesific, to keep track of which nodes that need to be treated

### BFS

Breadth-First-Search uses indegree to decide which nodes that should be taken out next
- Explores all the nodes on one level, and then moves on the the next level
- Uses a Fifo-queue (First in - first out) to keep track of which nodes that needs to be treated

<br>

## Shortest Path (Single Source)

Three algorithms for finding shortest paths from one source node to all other nodes:

| Algorithm | Handles negative weights | Handles negative cycles | Best for |
|---|---|---|---|
| **Dijkstra** | ❌ | ❌ | Fast, non-negative weights |
| **Bellman-Ford** | ✅ | Detects them | General graphs |
| **DAG Shortest Path** | ✅ | N/A (DAGs have no cycles) | Directed acyclic graphs |

<br>

## Shortest Path (All Pairs)

Algorithms that compute shortest paths between every pair of nodes:

- **Floyd-Warshall**: Classic O(V³) DP-based approach, easy to implement
- **Slow/Fast APSP**: Matrix-multiplication based approaches
- **Transitive Closure**: Boolean version — just checks if a path exists between every pair

<br>

## Other Algorithms

**Kosaraju's SCC** — Finds all strongly connected components in a directed graph. Uses two DFS passes: one on the original graph to record finish times, one on the transposed graph in reverse finish-time order.

**Kruskal's MST** — Builds a minimum spanning tree by greedily adding the cheapest edges that don't form a cycle. Uses Union-Find to detect cycles efficiently.

**Ford-Fulkerson (Edmonds-Karp)** — Finds the maximum flow through a network. Repeatedly finds augmenting paths using BFS (Edmonds-Karp variant), guaranteeing O(VE²) time.