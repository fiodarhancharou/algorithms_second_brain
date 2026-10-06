---
type: data-structure
tags: [data-structure, trie]
---
# Trie

## Operations
| Operation | Average | Worst |
|---|---|---|
| insert / search / startsWith | O(L) | O(L) |

L is the word length. Space is O(total characters).

## In Python
```python
class Trie:
    def __init__(self):
        self.root = {}

    def insert(self, word):
        node = self.root
        for ch in word:
            node = node.setdefault(ch, {})
        node["$"] = True               # end-of-word marker
```

## Use it when
- Prefix queries, autocomplete, word search on a grid with pruning.

## Patterns
- [[Backtracking]]
