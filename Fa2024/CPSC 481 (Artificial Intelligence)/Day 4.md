# Search algorithms
uninformed search
- exploring the problem space without any knowledge about the goal (getting closer? what area to search?)
- effective with smaller, simpler problem spaces
- ex: depth-first tree search
	a. root node A is first in the frontier stack
	b. push A's children B & C into the frontier stack
	c. pop C, explore its children

## Example problem
![[Pasted image 20230831145752.png]]![[Pasted image 20230831145923.png]]

<u>Depth-first search</u>
- Time complexity = $O(b^m)$
- Space complexity = $O(bm)$
	- m = depth; b = branching factor (children per node)
	- only space we use is for the frontier stack
	- **advantage**: uses less space compared to other methods
- Complete? **No**
	- can end up in **infinite loops** before exploring all pathsp
- Optimal? **No**
	- may explore a single path too far, skipping a more shallow path

<u>DFS with loop checking</u>
We now keep track of our current path, which will take up *m* spots in memory
- don't explore node if it's already did on our path
- mitigates loops

**Properties**
- Space complexity = $O(bm + m) \rightarrow O(bm)$
	- ($+m$) is negligible
Time complexity = $O(b^m)$
- Complete? **Yes (unless graph is infinite)**
- Optimal? **No**

<u>DF-Graph Search</u>
Keep track of **visited** nodes (as a **set**), in addition to our path
- add node to frontier ony if
	- it's not in the frontier, AND
	- it's not in the explored set

<u>Breadth-first graph search</u>
Like DF-graph, except frontier is now a **queue** (FIFO)

Example:
![[Pasted image 20230831160308.png]]![[Pasted image 20230831160337.png]]