---
type: pattern
tags: [pattern, graph, bfs, dfs]
---
# BFS and DFS

## Recognise it when
- Grid, graph, tree, or an implicit state graph.
- BFS: shortest path in an unweighted graph, level order.
- DFS: connected components, path existence, cycle detection, backtracking.

## Template
```python
from collections import deque

def bfs(graph, start):
    seen, q = {start}, deque([start])
    while q:
        node = q.popleft()
        for nxt in graph[node]:
            if nxt not in seen:
                seen.add(nxt)          # mark on enqueue, not on dequeue
                q.append(nxt)
    return seen

def dfs(graph, node, seen):
    seen.add(node)
    for nxt in graph[node]:
        if nxt not in seen:
            dfs(graph, nxt, seen)
```

## Complexity
- Time: O(V + E).
- Space: O(V) for `seen` and the queue or call stack.

## Pitfalls
- Marking visited on dequeue lets a node enter the queue many times.
- Recursive DFS can hit Python's recursion limit around 1000 frames; use an explicit stack.
- Cycle detection in a directed graph needs three states (unvisited, in-progress, done).

## Data structures
- [[Graph]], [[Queue and Deque]], [[Stack]], [[Tree]]

## Problems
- (none yet)
