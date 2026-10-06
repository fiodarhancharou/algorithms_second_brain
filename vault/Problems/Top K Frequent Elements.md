---
type: problem
tags: [problem, heap, hash]
difficulty: medium
pattern: ["[[Heap and Top-K]]", "[[Prefix Sums and Bucketing]]"]
time: O(n)
space: O(n)
status: solved
---
# Top K Frequent Elements

## Statement
Given an integer array `nums` and an integer `k`, return the `k` most frequent elements. Any order.

## Brute force: count, then sort
- Build a frequency map, sort its items by count descending, take the first `k`.
- Time: O(n) to count + O(m log m) to sort, where m is the number of unique elements. Worst case O(n log n).
- Space: O(m).

```python
def top_k_frequent_sort(nums, k):
    counter = {}
    for num in nums:
        counter[num] = counter.get(num, 0) + 1
    ranked = sorted(counter.items(), key=lambda x: x[1], reverse=True)
    return [key for key, _ in ranked[:k]]
```

## Better: min-heap of size k
- Keep only the k most frequent seen so far; the heap root is the weakest of them.
- Better than sorting when k is much smaller than the number of unique elements.
- Time: O(n) to count + O(m log k). Space: O(m) for the map, O(k) for the heap.

```python
import heapq

def top_k_frequent_heap(nums, k):
    counter = {}
    for num in nums:
        counter[num] = counter.get(num, 0) + 1
    heap = []
    for key, val in counter.items():
        heapq.heappush(heap, (val, key))
        if len(heap) > k:
            heapq.heappop(heap)
    return [key for _, key in heap]
```

## Optimal: bucket sort by frequency
- A frequency can be at most `n`, so make `n + 1` buckets where `buckets[i]` holds the elements that appear `i` times.
- Walk the buckets from the highest frequency down until `k` elements are collected.
- Time: O(n). Space: O(n).

```python
def top_k_frequent_bucket(nums, k):
    counter = {}
    for num in nums:
        counter[num] = counter.get(num, 0) + 1
    buckets = [[] for _ in range(len(nums) + 1)]
    for key, count in counter.items():
        buckets[count].append(key)
    res = []
    for count in range(len(buckets) - 1, 0, -1):
        res.extend(buckets[count])
        if len(res) >= k:
            return res[:k]
    return res
```

## Edge cases
- [ ] `k` equals the number of unique elements
- [ ] all elements equal
- [ ] ties at the cutoff (the problem usually guarantees a unique answer)
- [ ] negative numbers (fine as dict keys)

## Review
- The notebook version of the bucket loop used `while len(res) < k` with a negative index; that works only if `k` is valid. The `for` loop above cannot run off the end.
- Follow-ups: top k frequent words (tie-break alphabetically), k closest points, streaming version.

Related: [[Hash Map and Set]], [[Heap]]
