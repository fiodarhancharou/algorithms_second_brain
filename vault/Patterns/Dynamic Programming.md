---
type: pattern
tags: [pattern, dp]
---
# Dynamic Programming

## Recognise it when
- Overlapping subproblems plus optimal substructure.
- Count the ways, min or max cost, can-it-be-done over choices.
- A brute-force recursion that recomputes the same arguments.

## Template
1. Define the state in words ("dp[i] = fewest coins to make amount i").
2. Write the transition.
3. Set base cases.
4. Pick the order (top-down with memo, or bottom-up).
5. Shrink space if only the last row or few cells are needed.

```python
from functools import cache

@cache
def f(i):
    if i == 0:
        return base
    return best(f(i - step) for step in choices if i - step >= 0)
```

## Complexity
- Time: number of states x cost per transition.
- Space: number of states (often reducible).

## Pitfalls
- State too big or missing a dimension; the answer depends on something not in the state.
- Unreachable states need a sentinel such as `inf`, not 0.
- `@cache` on functions with mutable arguments fails; pass indices or tuples.

## Data structures
- [[Array and String]], [[Hash Map and Set]]

## Problems
- (none yet)
