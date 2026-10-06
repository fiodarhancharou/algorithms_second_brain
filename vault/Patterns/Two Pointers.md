---
type: pattern
tags: [pattern, two-pointers]
---
# Two Pointers

## Recognise it when
- Sorted array, or a structure you can walk from both ends.
- Pair or triplet that meets a condition (sum, distance).
- In-place partition or dedupe.

## Template
```python
def pair_with_sum(nums, target):      # nums sorted
    l, r = 0, len(nums) - 1
    while l < r:
        s = nums[l] + nums[r]
        if s == target:
            return l, r
        if s < target:
            l += 1
        else:
            r -= 1
    return None
```

## Complexity
- Time: O(n) after an O(n log n) sort if needed.
- Space: O(1).

## Pitfalls
- Requires sortedness (or a monotone property); otherwise use a hash map.
- For 3Sum, skip duplicates at all three positions.
- `l < r` vs `l <= r` depends on whether one element may pair with itself.

## Data structures
- [[Array and String]]

## Problems
- [[Triplets Within Distance d]] (the sorted-merge scan inside a bucket neighbourhood)
