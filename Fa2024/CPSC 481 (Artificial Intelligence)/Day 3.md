We create AI algorithms to solve a **variety** of problems. We want an algorithm that can be **generalized** to work towards some **goal**.

# State space search
a general problem solving strategy
- considers various **states** that occur throughout the solving process

*state*: **representation** for a problem solving step
- has available information and methods
*state space*: set of all possible states
*search*: algorithm for **exploring** the state space

Levels of state
- Conceptual/mental
- Symbolic
	- ie. drawings
- Computer
	- data structures
	- ie. arrays, tables, queue, etc.

Graph terms
- incidences
	- how many edges connected to a point
- adjacent
	- if two vertices are directly connected by an edge
- degree
	- how many edges a point has connected to it
- path
	- sequence of edges connected by vertices
- cycle
	- path which has the same start and end vertices
- frontier: set nodes on the frontline to immediately explore

*problem space*: a **graph** where states are *nodes* and operators are *edges*
*actions*: finite set of **actions** which can be executed on some state $s$
- `ACTIONS(s)`
*transition model*: **describes** what each action does
- `RESULT(s, a)`
*action cost function*: numeric **cost** of applying action `a` to state `s` to get state `s'`
- `ACTION_COST(s, a, s')`
![[Pasted image 20230829145820.png]]
Queues
- priority queue
	- nodes popped based on some priority
- FIFO queue
	- First-In First-Out: like a line at a store
- LIFO queue
	- Last-In First-Out: a stack

## Search strategies
Evaluating a strategy:
- completeness
- optimal (least-cost solution?)
- time/space complexity

Branching factor
- number of next states given some state
- number of children from a state tree node (don't count recursively)
- can vary between positions, levels: can be expressed as a math expression

