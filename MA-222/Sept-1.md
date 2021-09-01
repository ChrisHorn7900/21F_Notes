## Review of the lecture from August 30
- see notes taken on that day

# Sample Spaces and Events
- an event is a subset of outcomes contained in the sample space, that is, A is a subset of Ω
- an event is simple if it contains exactly one outcome
    - example: if Ω = {w1,w2,...,wn} then {w1} is a subset of Ω is a simple event
- an event is compound if it contains more than one outcome
- we say an event A occurs if the outcome of the experiment is contained in A
- if |Ω| = n then the numver of all possible events is 2^n (powerset)
    - example: Ω = {1,2,3,4,5,6}. All possible events? if we get a 1 what events occurred?
    - example: A = "obtain an odd number"
- **Conceptually, an outcome is a point and an event is a set (very different!)**

# Set Operations
- outcome is a point, event is a set
- **complement** of A denoted by A' (or A bar) is the set of outcomes not contained in A
    - roll a dice: A="get a 1"
- some properties: (A')' = A, Ω' = empty set
- venn diagram
- **Union** of two events A, B denoted by A union B is the set of all outcomes that are either in A or B or in both. All outcomes in at least one of the events.
    - Example: A = "get <=2", B="get >=4"
- A U empty set = A, A U A = A, A U A' = ?
- **Intersection** of two events A, B denoted by A intersects B is the set of all outcomes that are in both A and B
A intersects empty set = ?, A intersects A = A, A intersects A' = ?
- **empty set** (null event), denoted by empty set is the event consisting of no outcomes whatsoever (nothing happens)
- all possible events are given by complements and unions (see sigma algebra definition if interested in more)
- **Mutually exclusive events** A intersects B = empty set (cannot happen at the same time)

