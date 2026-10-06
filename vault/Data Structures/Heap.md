---
type: data-structure
tags: [data-structure, heap, priority-queue]
---
# Heap

## Operations
| Operation | Average | Worst |
|---|---|---|
| push | O(log n) | O(log n) |
| pop min | O(log n) | O(log n) |
| peek min | O(1) | O(1) |
| heapify a list | O(n) | O(n) |
| `nlargest(k, xs)` | O(n log k) | O(n log k) |

## In Python
```python
import heapq

h = [5, 1, 4]
heapq.heapify(h)                       # in place, min-heap
heapq.heappush(h, 2)
smallest = heapq.heappop(h)
heapq.heappush(h, (-score, item))      # max-heap trick: negate the key
heapq.nlargest(3, h)
```

## Use it when
- Repeated access to the current min or max.
- Top-k, k-way merge, scheduling, Dijkstra.

## Patterns
- [[Heap and Top-K]], [[Intervals]]
