---
type: pattern
tags: [pattern, floyd, cycle-detection]
---
# Fast and Slow Pointers

## Recognise it when
- A cycle in a linked list, or in a sequence defined by `x -> f(x)`.
- Middle of a linked list.
- Array of n+1 values in `1..n`, which is a hidden linked list ([[Find the Duplicate Number]]).

## Template (Floyd's)
```python
def cycle_entry(next_of, start):
    slow = fast = start
    while True:                        # phase 1: meet inside the cycle
        slow = next_of(slow)
        fast = next_of(next_of(fast))
        if slow == fast:
            break
    slow = start                       # phase 2: walk both at speed 1
    while slow != fast:
        slow, fast = next_of(slow), next_of(fast)
    return slow                        # the cycle entry
```

## Why it works
Let the tail be `a` steps and the cycle length `c`. At the meeting point, fast has travelled twice as far as slow, so the distance slow has walked is a multiple of `c`. Starting a second pointer from the head and walking both one step at a time, they meet exactly at the cycle entry.

## Complexity
- Time: O(n).
- Space: O(1).

## Pitfalls
- Phase 1 for a linked list must guard `fast` and `fast.next` for None; the array version has no None.
- Do not skip phase 2 if you need the entry, not just whether a cycle exists.

## Data structures
- [[Linked List]], [[Array and String]]

## Problems
- [[Find the Duplicate Number]]
