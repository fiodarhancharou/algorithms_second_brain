---
type: problem
tags: [problem, bucketing, streaming]
difficulty: medium
pattern: ["[[Prefix Sums and Bucketing]]", "[[Two Pointers]]"]
time: see complexity
space: O(numbers kept in memory)
status: solved
---
# Triplets Within Distance d

## Statement
Numbers arrive one at a time as a stream. After each number, report a triplet `(a, b, c)` from the numbers held in memory where all pairwise distances are at most `d` (`|a-b| <= d`, `|b-c| <= d`, `|a-c| <= d`), or `None`. When a triplet is found, those three numbers are consumed (removed from memory).

Since the span of three sorted numbers is `max - min`, the condition reduces to `max - min <= d`.

## Examples worked by hand
`d = 10.1`, inputs `2, 1, 100, 3, 4, 2, 3`:
- `2` -> None, memory `[2]`
- `1` -> None, memory `[2, 1]`
- `100` -> None, memory `[2, 1, 100]`
- `3` -> `(1, 2, 3)`, memory `[100]`
- `4` -> None, memory `[100, 4]`
- `2` -> None, memory `[100, 4, 2]`
- `3` -> `(2, 3, 4)`, memory `[100]`

## Key insight
Bucket each number by `num // d`. Any number within distance `d` of `num` must be in bucket `b - 1`, `b`, or `b + 1`, so only those three buckets need to be inspected, never the whole memory. Merge them, sort, and slide a window of three; the first window with `last - first <= d` is a triplet.

```python
from collections import defaultdict


class TripletFinder:
    def __init__(self, d):
        self.d = d
        self.holder = defaultdict(list)

    def find_triplets(self, num):
        b = num // self.d
        merged = sorted(
            self.holder[b - 1] + self.holder[b] + self.holder[b + 1] + [num]
        )
        for l in range(len(merged) - 2):
            r = l + 2
            if merged[r] - merged[l] <= self.d:
                triplet = merged[l : r + 1]
                stored = triplet[:]
                stored.remove(num)  # drop exactly one copy: the new arrival, never stored
                for x in stored:
                    self.holder[x // self.d].remove(x)
                return triplet
        self.holder[b].append(num)
        return None
```

## Complexity
- Time per number: O(m log m), where m is the count held in the three neighbouring buckets. If the data is spread out, m is small; if many values pile into one bucket, it degrades. Removing from a bucket list is O(m) too.
- Space: O(numbers kept in memory).

## Edge cases and tests
Test cases that the notebook's harness covers:
- [x] the walkthrough above
- [x] exact boundary, diff equals `d` must count
- [x] values too spread out for any triple
- [x] negative numbers spanning zero
- [x] floats and a non-integer `d`
- [x] memory after a match is reusable later
- [x] duplicates equal to `num`: `3, 3, 3, 3` with `d = 10` must give a triplet on the third input and `None` on the fourth

## Review
- Bug found while writing this note: the original `if x != num` guard skipped *every* stored copy equal to the new number, so stale duplicates stayed in memory and were reused by the next input. The code above removes exactly one copy of `num` from the triplet instead.
- Hint that unlocked it: `floor(input / d)`.
- To drill: reasoning about the bucket-neighbour argument out loud; the cost when one bucket grows large (a sorted container would fix it).
- Follow-ups: groups of size k, sliding time window instead of consume-on-match.

Related: [[Hash Map and Set]], [[Array and String]]
