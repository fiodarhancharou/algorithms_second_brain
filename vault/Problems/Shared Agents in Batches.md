---
type: problem
tags: [problem, hash, set]
difficulty: easy
pattern: []
time: O(total entries)
space: O(distinct agents)
status: solved
---
# Shared Agents in Batches

## Statement
Given a list of batches, where each batch is a list of dicts with `"agent"` and `"task"` keys, and a target `key`, return the set of distinct agents that share at least one batch with `key`, excluding `key` itself.

## Example
Batches 1 and 3 contain `AgentC`. Batch 1 has `{A, C}`, batch 3 has `{D, C, A}`, so the answer is `{AgentA, AgentD}`. `AgentB` only appears in batch 2.

## Approach
- Reduce each batch to the set of its agents.
- If the target is in that set, union the set into the result.
- Remove the target at the end.

```python
def find_shared_agents(batches, key):
    result = set()
    for batch in batches:
        agents = {entry["agent"] for entry in batch}
        if key in agents:
            result |= agents
    result.discard(key)
    return result
```

## Complexity
- Time: O(N), N is the total number of entries across batches.
- Space: O(A), A is the number of distinct agents.

## Edge cases
- [ ] key appears in no batch, so the result is empty
- [ ] key appears twice in one batch
- [ ] empty batches
- [ ] a batch containing only the key

## Review
- `discard` avoids a KeyError when the key was never added; the notebook's `result - {key}` is also safe.
- Follow-up: a graph view, where agents are nodes and a shared batch is an edge, leading to "agents within 2 hops".

Related: [[Hash Map and Set]]
