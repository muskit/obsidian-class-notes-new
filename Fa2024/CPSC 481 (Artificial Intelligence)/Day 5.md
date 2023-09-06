## Search algorithms cont.
Depth-limited DFS
- we mitigate not being complete to infinite spaces by adding **depth limit** $l$
- requires knowing what the depth of solution is
- Time & Space complexity doesn't change

Iterative Deepening
- go down one depth a time until a solution is found
	- DFS $l=1$
	- solution found? stop. otherwise, DFS $l=2$
	- solution found? stop. otherwise, DFS $l=3$
	- solution found? stop. otherwise, etc.
- balance between DFS and BFS
- Time complexity: $O(b^d)$
	- same as BFS
- Space complexity: $O(bm)$
	- same as DFS (advantagous)
- **the preferred uninformed search method for large, unknown-depth search space**

**Space is a bigger issue than time**
 - \# of nodes grows extremely quickly (exponentially) as we go deeper in the search space
 - ways to avoid tracking so many nodes have been devised, including *Dijkstra's algorithm*

## Dijkstra's Algorithm
recall: *frontier*- set of nodes ready/waiting to be immediately explored

**Uniform cost search (variation of Dijkstra's)**
Data structures:
- frontier: `priority queue[node]` (ordered by path cost)
- explored ("closed"): `set[node]`
Algorithm:
```python
frontier = # some initial state
explored = set()
while True:
	if frontier.empty: return FAILURE
	cand = frontier.pop() # get lowest cost node
	if cand == goal: return SUCCESS
	explored.add(cand)
	for child in cand:
		# set candidate in frontier only if it's lower than in the frontier if it exists
		if child not in frontier or child not in explored:
			frontiner.add(cand)
		elif child in frontier \
			and frontier[child].cost > cand[child].cost:
			frontier[child] = child
```

Example
![[Pasted image 20230905152309.png]]![[Pasted image 20230905152336.png]]
- Goal and C have the same weight in the frontier. Which one gets popped depends on the data structure implementation

UCS/Dijkstra's **does not have a goal in mind**. They search for the shortest path from the start to every other node, effectively producing a new graph.

Space complexity: $O(b^{C*/\epsilon})$
The Good: UCS/Dijkstra's is **complete** and **optimal**.
The Bad: explores **everything**, no goal considered

# The search algorithms we have so far
Breadth-First Search (BFS) - expands shallowest node
Depth-First Search (DFS) - expands deepest node
Depth-Limited Search (DLS) - DFS w/ depth limit
Iterative-Deepening Search (IDS) - DLS w/ increasing limit
Uniform-Cost Search (UCS) - expands least-cost node