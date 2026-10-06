---
type: data-structure
tags: [data-structure, hash]
---
# Hash Map and Set

## Operations
| Operation | Average | Worst |
|---|---|---|
| insert / delete / lookup | O(1) | O(n) |
| iterate | O(n) | O(n) |

## In Python
```python
from collections import Counter, defaultdict

counts = Counter(nums)                 # frequency map
groups = defaultdict(list)             # group by key
seen = set()
if x in seen: ...                      # O(1) membership
```

## Use it when
- You need O(1) membership or "have I seen the complement?" (Two Sum).
- Counting frequencies, grouping, deduplicating.
- Keys must be hashable: tuples yes, lists no.

## Patterns
- [[Heap and Top-K]], [[Prefix Sums and Bucketing]], [[Sliding Window]], [[Dynamic Programming]]
