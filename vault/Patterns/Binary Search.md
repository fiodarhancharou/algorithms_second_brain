---
type: pattern
tags: [pattern, binary-search]
---
# Binary Search

## Recognise it when
- Sorted input, or a monotone predicate (false...false true...true).
- "Minimum X such that condition holds" (search on the answer).
- Asked for O(log n).

## Template
```python
def first_true(lo, hi, pred):
    """Smallest x in [lo, hi] with pred(x) True; hi+1 if none."""
    while lo <= hi:
        mid = (lo + hi) // 2
        if pred(mid):
            hi = mid - 1
        else:
            lo = mid + 1
    return lo
```

## Complexity
- Time: O(log n) probes, times the cost of each probe.
- Space: O(1).

## Pitfalls
- Off-by-one on the loop bound and on `mid +/- 1`; pick one invariant and stick to it.
- Python has no overflow, but other languages need `lo + (hi - lo) // 2`.
- `bisect_left` / `bisect_right` already cover the common cases.

## Data structures
- [[Array and String]]

## Problems
- (none yet)
