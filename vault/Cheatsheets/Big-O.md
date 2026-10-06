---
type: cheatsheet
tags: [cheatsheet, complexity]
---
# Big-O cheat sheet

## Growth order (best to worst)
O(1) < O(log n) < O(n) < O(n log n) < O(n^2) < O(2^n) < O(n!)

## Input size to complexity hint (about 1 second)
| n | Likely target |
|---|---|
| <= 10-12 | O(n!) or O(2^n * n), [[Backtracking]] |
| <= 20-25 | O(2^n) |
| <= 500 | O(n^3) |
| <= 5,000 | O(n^2) |
| <= 10^5-10^6 | O(n log n) or O(n) |
| >= 10^9 | O(log n) or O(1), [[Binary Search]] or math |

## Python built-ins
| Operation                      | Cost                          |
| ------------------------------ | ----------------------------- |
| `list.append` / `pop()`        | O(1)                          |
| `list.pop(0)` / `insert(0, x)` | O(n), use [[Queue and Deque]] |
| `x in list`                    | O(n)                          |
| `x in set` / `dict`            | O(1) average                  |
| `sorted` / `list.sort`         | O(n log n)                    |
| `heapq.heappush` / `heappop`   | O(log n)                      |
| `heapq.heapify`                | O(n)                          |
| slice `a[i:j]`                 | O(j - i)                      |
| `s += c` in a loop             | O(n^2) total                  |
| `"".join(parts)`               | O(total length)               |

## Typical patterns
| Pattern | Time | Space |
|---|---|---|
| [[Sliding Window]] | O(n) | O(k) |
| [[Two Pointers]] on sorted input | O(n) | O(1) |
| [[Binary Search]] | O(log n) | O(1) |
| [[BFS and DFS]] | O(V + E) | O(V) |
| [[Topological Sort]] | O(V + E) | O(V + E) |
| [[Heap and Top-K]] | O(n log k) | O(k) |
| [[Dynamic Programming]] | states x transitions | states |
| [[Backtracking]] subsets / permutations | O(2^n) / O(n!) | O(n) |

## Reminders
- Recursion uses O(depth) stack space.
- Amortised O(1) append: occasional O(n) resize, O(1) on average.
- Say both time and space, and say what n is.
