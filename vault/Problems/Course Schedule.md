---
type: problem
tags: [problem]
difficulty:
pattern: []
time:
space:
status: todo
---
# Course Schedule

## Statement

You are given an array `prerequisites` where `prerequisites[i] = [a, b]` indicates that you **must** take course `b` first if you want to take course `a`.

The pair `[0, 1]`, indicates that must take course `1` before taking course `0`.

There are a total of `numCourses` courses you are required to take, labeled from `0` to `numCourses - 1`.

Return `true` if it is possible to finish all courses, otherwise return `false`.

**Example 1:**

```java
Input: numCourses = 2, prerequisites = [[0,1]]

Output: true
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
def canFinish(self, numCourses: int, prerequisites: List[List[int]]) -> bool:
	# Kahn's algorithm
	n_prereqs = [0]*numCourses
	node_parents = [[] for i in range(numCourses)]
	for a, b in prerequisites:
		node_parents[b].append(a)
		n_prereqs[a] += 1
	q = deque(i for i, n in enumerate(n_prereqs) if n == 0)
	count = 0
	while q:
		course = q.popleft()
		count += 1
		for parent in node_parents[course]:
			n_prereqs[parent] -= 1
			if n_prereqs[parent] == 0:
				q.append(parent)
	return count == numCourses
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
