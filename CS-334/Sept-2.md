### see slides or something for tennis match automaton

# Where are we headed?
- given a finite stae machine diagram, what language does it accept?
- given a language, can it be recognized by a finite state machine?
    - if yes: design a DFA for the language
        - minimize the number of states of the DFA
    - if not: prove it!

# Finite State Machines: Terminology
From each state there must be a state **transition** for every symbol in the alphabet. The machine **accepts** a string if, beginning with the start state and following the transitions corresponding to successive symbols in the string, the machine ends in an accept state. If not, the machine rejects the string.

# Getting formal

- a finite automaton M is a 5-tuple (Q,Σ,δ,q0,F)
    - Q is the finite set of states
    - Σ is the finite alphabet of symbols
    - δ:Q x Σ → Q is the state transition **function**
    - q0 is the start state
    - F is the set of accept states

# Formal Definition 2
- A finite automaton M = (Q,Σ,δ,q0,F) **accepts** a string w = w1w2...wn if there is a sequence r0, r1, ..., rn of states in Q such that:
    1. r0 = q0, (start in the start state)
    2. ri+1 = δ(ri, wi+1) for 0 ≤ i ≤ n, and (every transition is legal)
    3. rn ε F. (the final state is an accept state)
    
# Designing Finite Automata
### Problem: Design a DFA for the language {w:w ends in 000}
- pretend that you are the DFA
    - the input string is revealed one symbol at a time. When you see symbol you must decide the next state. You must be in an accept state **iff** ...

# Searching for a pattern in a text string
- Find all occurrences of "Ali Bashir" or "Colin Creevey" in the text of Harry Potter and the Goblet of Fire
- Step 1: Design a DFA to recognize the language {Ali Bashir, Colin Creevey}
- Step 2: Run the text of Harry Potter and the Goblet of Fire (the input string) through the DFA. Each time you enter an accept state, print the position in the text.
**DFA theory is the basis of pattern search**

# Regular Operations on Languages
- Let A, B be two languages (set of strings over alphabets)
- **Union** A U B = {w:w ε A or w ε B}
- **Concatenation** A ○ B = {w1w2: w1 ε A and w2 ε B}
- **Star** A* = {w: }

# Our First Theorem
- Suppose that A, B are both regular languages
- What about A U B?
- **Theorem 1.25** The class of regular languages is closed under the union operation. In other words, if A, B are both regular languages then A U B is regular as well
- Why might this be useful?
    - In designing a DFA for language L it's sometimes easier to express L = A U B,
    - Next design separate DFAs for A and B, and
    - Finally combine the two DFAs to make a DFA for L.