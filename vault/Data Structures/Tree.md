---
type: data-structure
tags: [data-structure, tree, bst]
---
# Tree

## Operations
| Operation | Average | Worst |
|---|---|---|
| BST search / insert / delete | O(log n) | O(n) when skewed |
| traversal (pre, in, post, level) | O(n) | O(n) |

## In Python
```python
class TreeNode:
    def __init__(self, val=0, left=None, right=None):
        self.val, self.left, self.right = val, left, right

def height(node):
    return 0 if not node else 1 + max(height(node.left), height(node.right))
```

## Use it when
- Hierarchical data; BST inorder gives sorted order.
- Most tree problems are a DFS that returns a value from each subtree.
- Recursion depth equals tree height: O(n) for a skewed tree.

## Patterns
- [[BFS and DFS]]
