---
type: cheatsheet
tags: [cheatsheet, python]
---
# Python for interviews

## Collections
```python
from collections import Counter, defaultdict, deque
import heapq, bisect

Counter("aabc")                        # Counter({'a': 2, 'b': 1, 'c': 1})
d = defaultdict(list); d[k].append(v)
q = deque(); q.append(x); q.popleft()
```

## Heap
```python
a = [1, 2, 3, 4, 5]
heapq.heapify(a)                       # in place, min-heap
heapq.nlargest(6, a)                   # returns all 5 if k > len
heapq.nsmallest(2, a)
```
See [[Heap]].

## Sorting
```python
sorted(pairs, key=lambda x: (x[0], x[1]))     # multi-key
sorted(pairs, key=lambda x: (x[0], -x[1]))    # asc then desc
a.sort()                                       # in place, returns None
```

## Characters and numbers
```python
ord("B") - ord("A")                    # 1, index of a letter
chr(ord("a") + 3)                      # 'd'
sum([])                                # 0, safe on empty
list(range(7, 5, -1))                  # [7, 6]
list(range(-1))                        # [], empty range is not an error
"asdf0"[4]                             # '0', IndexError if out of range
```

## Gotchas
- `queue.Queue` is the thread-safe queue; use `collections.deque` for algorithms.
- A `range(a, b)` with `a >= b` is empty.
- `a // d` floors toward negative infinity (relevant for [[Prefix Sums and Bucketing]]).
- Lists are not hashable; use tuples as dict keys.
- `help(obj)` in a notebook is the fastest way to recall a signature.
