---
type: pattern
tags: [pattern, intervals]
---
# Intervals

## Recognise it when
- Ranges `[start, end]`: merge, insert, overlap, meeting rooms.

## Template
```python
def merge(intervals):
    intervals.sort(key=lambda x: x[0])
    out = [intervals[0]]
    for start, end in intervals[1:]:
        if start <= out[-1][1]:                  # overlap
            out[-1][1] = max(out[-1][1], end)
        else:
            out.append([start, end])
    return out
```

## Complexity
- Time: O(n log n) for the sort.
- Space: O(n) for the output.

## Pitfalls
- Sort first; almost everything depends on it.
- Use `max` for the merged end; one interval can swallow the next.
- Decide whether touching intervals (`end == start`) overlap.

## Data structures
- [[Array and String]], [[Heap]] (meeting rooms)

## Problems
- (none yet)
