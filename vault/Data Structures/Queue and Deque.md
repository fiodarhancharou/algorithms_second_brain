---
type: data-structure
tags: [data-structure, queue, deque]
---
# Queue and Deque

## Operations
| Operation | Average | Worst |
|---|---|---|
| append / appendleft | O(1) | O(1) |
| pop / popleft | O(1) | O(1) |
| index in the middle | O(n) | O(n) |

## In Python
```python
from collections import deque

q = deque()
q.append(1); q.append(2)
q.popleft()                            # O(1); list.pop(0) is O(n)
len(q)
```

## Use it when
- BFS frontier, level-order traversal.
- Sliding window maximum (monotonic deque).
- `queue.Queue` is for threads; use `deque` for algorithms.

## Patterns
- [[BFS and DFS]], [[Topological Sort]], [[Sliding Window]]
