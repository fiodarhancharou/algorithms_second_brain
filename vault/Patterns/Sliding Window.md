---
type: pattern
tags: [pattern, sliding-window]
---
# Sliding Window

## Recognise it when
- Contiguous subarray or substring with a constraint (longest, shortest, count).
- The constraint can be checked incrementally as elements enter and leave.

## Template
```python
def longest_valid(s):
    left = best = 0
    state = {}  # whatever tracks the window
    for right, ch in enumerate(s):
        state[ch] = state.get(ch, 0) + 1          # expand
        while not valid(state):                    # shrink until valid again
            state[s[left]] -= 1
            left += 1
        best = max(best, right - left + 1)
    return best
```

## Complexity
- Time: O(n), each index enters and leaves the window once.
- Space: O(k) for the window state.

## Pitfalls
- Update `best` after shrinking, not before.
- Fixed-size windows need no `while`, only an `if` that evicts one element.
- Shrinking with `while` vs `if` changes correctness for variable windows.

## Data structures
- [[Hash Map and Set]], [[Queue and Deque]] (monotonic deque for window max/min)

## Problems
- Longest Substring Without Repeating Characters (not yet in the vault)
- [[Triplets Within Distance d]] (a streaming cousin: window over a value range)
