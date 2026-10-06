---
type: data-structure
tags: [data-structure, linked-list]
---
# Linked List

## Operations
| Operation | Average | Worst |
|---|---|---|
| insert / delete at a known node | O(1) | O(1) |
| access by index / search | O(n) | O(n) |

## In Python
```python
class ListNode:
    def __init__(self, val=0, next=None):
        self.val, self.next = val, next

dummy = ListNode()                     # dummy head removes head special cases
```

## Use it when
- Interview problems about pointer manipulation: reverse, merge, detect a cycle.
- Tricks: dummy head, fast and slow pointers, reverse in place.

## Patterns
- [[Fast and Slow Pointers]], [[Two Pointers]]
