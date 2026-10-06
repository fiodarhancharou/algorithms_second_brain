---
type: pattern
tags: [pattern, graph, topological-sort]
---
# Topological Sort

## Recognise it when
- Dependencies or prerequisites between items.
- "Can all tasks be completed?" means cycle detection in a directed graph.

## Template (Kahn's algorithm)
```python
from collections import deque

def topo_order(n, edges):
    adj = [[] for _ in range(n)]
    indeg = [0] * n
    for a, b in edges:                 # a must come before b
        adj[a].append(b)
        indeg[b] += 1
    q = deque(i for i in range(n) if indeg[i] == 0)
    order = []
    while q:
        node = q.popleft()
        order.append(node)
        for nxt in adj[node]:
            indeg[nxt] -= 1
            if indeg[nxt] == 0:
                q.append(nxt)
    return order if len(order) == n else []   # [] means a cycle exists
```

## Complexity
- Time: O(V + E).
- Space: O(V + E).

## Pitfalls
- Edge direction: read the statement carefully (prerequisite pair `[a, b]` often means b -> a).
- A shorter output than `n` means a cycle.

## Data structures
- [[Graph]], [[Queue and Deque]]

## Problems
- (none yet)
