---
type: problem
tags: [problem, floyd, cycle-detection]
difficulty: medium
pattern: ["[[Fast and Slow Pointers]]"]
time: O(n)
space: O(1)
status: solved
---
# Find the Duplicate Number

## Statement
`nums` has `n + 1` integers, each in `[1, n]`. Exactly one value repeats (possibly many times). Return it without modifying the array and using O(1) extra space.

## Key insight
Treat the array as a linked list where index `i` points to `nums[i]`. Because there are `n + 1` slots and only values `1..n`, some node has two incoming edges, so a cycle exists, and the **cycle entry is the duplicate**. Value 0 is never a target, so starting at index 0 always reaches the cycle.

## Approach: Floyd's two phases
1. Slow moves one step, fast moves two, until they meet inside the cycle.
2. Reset slow to the start; move both one step at a time. They meet at the cycle entry.

```python
def find_duplicate(nums):
    slow = fast = 0
    while True:
        slow = nums[slow]
        fast = nums[nums[fast]]
        if slow == fast:
            break
    slow = 0
    while slow != fast:
        slow = nums[slow]
        fast = nums[fast]
    return slow
```

Worked example `[1, 2, 4, 4, 3]`: the chain from 0 is `0 -> 1 -> 2 -> 4 -> 3 -> 4 -> ...`. The cycle is `4 -> 3 -> 4`, entered at 4, which is the duplicate.

## Complexity
- Time: O(n). Space: O(1).
- Alternatives: set (O(n) space), sort (O(n log n), mutates), binary search on value range (O(n log n), O(1) space).

## Edge cases
- [ ] duplicate appears more than twice
- [ ] duplicate is the first or last element
- [ ] n = 1, so `[1, 1]`

## Review
- Be ready to justify phase 2: see "Why it works" in [[Fast and Slow Pointers]].
- Follow-ups: Linked List Cycle II, Happy Number.

Related: [[Linked List]]
