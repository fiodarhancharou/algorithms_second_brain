---
type: pattern
tags: [pattern, prefix-sum, bucketing]
---
# Prefix Sums and Bucketing

Two related ideas: precompute to answer range queries fast, and group values into buckets so that only nearby buckets need inspecting.

## Recognise it when
- Many range-sum queries, or subarray sum equals k (prefix sum plus hash map).
- Frequencies are bounded by n: bucket by count and avoid sorting.
- A distance constraint `|a - b| <= d`: bucket by `value // d`, so only the same and adjacent buckets can hold matches.

## Template
```python
# prefix sums
prefix = [0]
for x in nums:
    prefix.append(prefix[-1] + x)
range_sum = prefix[j + 1] - prefix[i]          # sum of nums[i..j]

# bucket by frequency
buckets = [[] for _ in range(len(nums) + 1)]
for value, count in counter.items():
    buckets[count].append(value)

# bucket by distance
bucket = num // d                              # neighbours live in bucket-1, bucket, bucket+1
```

## Complexity
- Time: O(n) to build; O(1) per query or per bucket lookup.
- Space: O(n).

## Pitfalls
- Prefix array has length n + 1 so the empty prefix is index 0.
- Floor division of negatives in Python rounds down, which is what bucketing needs.
- A bucket width of `d` means matches can sit one bucket away, so check three buckets.

## Data structures
- [[Hash Map and Set]], [[Array and String]]

## Problems
- [[Top K Frequent Elements]] (frequency buckets)
- [[Triplets Within Distance d]] (distance buckets)
