---
type: problem
tags:
  - problem
difficulty: medium
pattern:
  - backtracking
time:
space:
status: todo
---
# Permutations

## Statement

Given an array `nums` of **unique** integers, return all the possible permutations. You may return the answer in **any order**.

**Example 1:**

```Python
Input: nums = [1,2,3]

Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],
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
def permute(self, nums: List[int]) -> List[List[int]]:
	result = []
	def backtrack(arr, used_nums):
		if len(arr) == len(nums):
			result.append(arr[:])
			return
		
		for i in range(len(nums)):
			if nums[i] not in used_nums:
				arr.append(nums[i])
				used_nums.add(nums[i])
				backtrack(arr, used_nums)
				used_nums.remove(nums[i])
				arr.pop()

		backtrack([], set())
		return result
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
