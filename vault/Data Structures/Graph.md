---
type: data-structure
tags: [data-structure, graph]
---
# Graph

## Operations
| Representation | Space | Edge lookup | Iterate neighbours |
|---|---|---|---|
| adjacency list | O(V + E) | O(deg) | O(deg) |
| adjacency matrix | O(V^2) | O(1) | O(V) |

## In Python
```python
from collections import defaultdict

adj = defaultdict(list)
for a, b in edges:
    adj[a].append(b)
    adj[b].append(a)                   # drop this line for a directed graph
```

## Use it when
- Relationships, dependencies, grids (each cell is a node with up to 4 neighbours).
- Default to an adjacency list; the matrix only for small dense graphs.

## Patterns
- [[BFS and DFS]], [[Topological Sort]]
