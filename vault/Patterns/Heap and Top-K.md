---
type: pattern
tags: [pattern, heap, top-k]
---
# Heap and Top-K

## Recognise it when
- "k largest / smallest / most frequent".
- A stream where you repeatedly need the current min or max.
- Merging k sorted sources.

## Template
```python
import heapq

def top_k_largest(nums, k):
    heap = []                          # min-heap of size k
    for x in nums:
        heapq.heappush(heap, x)
        if len(heap) > k:
            heapq.heappop(heap)        # drop the smallest of the k+1
    return heap                        # heap[0] is the kth largest
```

## Complexity
- Time: O(n log k), better than sorting when k << n.
- Space: O(k).
- Bucket sort gives O(n) when the key is a bounded count (see [[Prefix Sums and Bucketing]]).

## Pitfalls
- `heapq` is a min-heap only; negate values for a max-heap.
- To keep the k largest, use a min-heap of size k (counter-intuitive).
- Tuples compare element by element; ties fall through to the second field.

## Data structures
- [[Heap]], [[Hash Map and Set]]

## Problems
- [[Top K Frequent Elements]]
