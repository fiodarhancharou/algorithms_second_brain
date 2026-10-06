---
type: problem
tags: [problem]
difficulty:
pattern: []
time:
space:
status: todo
---
# # Kth Largest Element in an Array

## Statement

Given an unsorted array of integers `nums` and an integer `k`, return the `kth` largest element in the array.

By `kth` largest element, we mean the `kth` largest element in the sorted order, not the `kth` distinct element.

Follow-up: Can you solve it without sorting?

**Example 1:**

```java
Input: nums = [2,3,1,5,4], k = 2

Output: 4
```

## Examples worked by hand

## Brute force
- Approach:
- Time / Space:

## Optimised approach
- Key insight:
- Pattern: [[]]
- Time / Space:

```python
import heapq

def findKthLargest(self, nums: List[int], k: int) -> int:
	heap = []
	for num in nums:
		heapq.heappush(heap, num)
		if len(heap) > k:
			heapq.heappop(heap)
	return heap[0]
```

## Edge cases
- [ ] empty input
- [ ] single element
- [ ] duplicates
- [ ] negative numbers
- [ ] all-same values

## Review
- What went well:
- What to drill:
- Follow-up variants:
