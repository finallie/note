#

|Search Time| Space| When to use
|---|---|---
|DFS |O(c^k^) |O(k) Must search tree anyway, know the level the answers are on, or you aren't looking for the shallowest number.
|BFS |O(c^d^) |O(c^d^)| Know answers are very near top of tree, or want shallowest answer.
|DFS+ID |O(c^d^) |O(d)| Want to do BFS, don't have enough space, and can spare the time.

d is the depth of the answer

k is the depth searched

d <= k
