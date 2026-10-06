---
type: data-structure
tags: [data-structure, array, string]
---
# Array and String

## Operations
| Operation | Average | Worst |
|---|---|---|
| index access | O(1) | O(1) |
| append | O(1) amortised | O(n) on resize |
| insert / delete in the middle | O(n) | O(n) |
| `pop(0)` / `insert(0, x)` | O(n) | O(n) |
| slice `a[i:j]` | O(j - i) | O(j - i) |
| sort | O(n log n) | O(n log n) |

## In Python
```python
nums.sort(key=lambda x: (x[0], -x[1]))     # stable, in place
s = "".join(parts)                          # not += in a loop
ord("b") - ord("a")                         # 1, char to index
```

## Use it when
- Default container; random access by index.
- Strings are immutable: building char by char in a loop is O(n^2), so collect and join.

## Patterns
- [[Two Pointers]], [[Sliding Window]], [[Binary Search]], [[Intervals]], [[Prefix Sums and Bucketing]], [[Backtracking]]
