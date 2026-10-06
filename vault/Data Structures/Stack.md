---
type: data-structure
tags: [data-structure, stack]
---
# Stack

## Operations
| Operation | Average | Worst |
|---|---|---|
| push / pop / peek | O(1) | O(1) |

## In Python
```python
stack = []
stack.append(x)
top = stack[-1]
stack.pop()
```

## Use it when
- Matching brackets, undo, evaluating expressions.
- Monotonic stack: next greater element, histogram problems.
- Iterative DFS, replacing recursion.

## Patterns
- [[BFS and DFS]], [[Backtracking]]
