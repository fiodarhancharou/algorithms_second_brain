---
type: pattern
tags: [pattern, backtracking]
---
# Backtracking

## Recognise it when
- Generate all subsets, permutations, combinations, or valid configurations.
- A decision tree where partial choices can be pruned.

## Template
```python
def subsets(nums):
    res, path = [], []
    def go(i):
        if i == len(nums):
            res.append(path[:])        # copy, the path keeps mutating
            return
        go(i + 1)                      # skip nums[i]
        path.append(nums[i])           # choose
        go(i + 1)
        path.pop()                     # undo
    go(0)
    return res
```

## Complexity
- Time: usually exponential, such as O(2^n) for subsets and O(n!) for permutations.
- Space: O(n) recursion depth, plus output.

## Pitfalls
- Append a copy of the path, not the path itself.
- Always undo the choice on the way back.
- Prune early (sort, skip duplicates, bound checks) to cut the tree.

## Data structures
- [[Array and String]], [[Stack]] (the call stack)

## Problems
- [[Permutations]]
