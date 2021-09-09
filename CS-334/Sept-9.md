## Administrivia
- read section 1.3 of the textbook

## Example NFA N
- (see slides for nondeterministic machine n)
- What is the language L(N)? {w:w has at least 2 symbols and either the second last or third last symbol is 1}

        N = (Q,Σ,δ,q0,F) where:
            Q = {A, B, C, D}            δ(A,0) = {A}        δ(C,0) = {D}
            Σ = {0, 1}                  δ(A,1) = {A,B}      δ(C,1) = {D}
            q0 = A                      δ(A,ε) = φ          δ(C,ε) = φ
            F = {D}                     δ(B,0) = {C}        δ(D,0) = φ
                                        δ(B,1) = {C}        δ(D,1) = φ
                                        δ(B,ε) = {C}        δ(D,ε) = φ

## Designing a DFA Equivalent to NFA N

- M = (Q',Σ',δ',q0',F') where
        Σ' = Σ

- What states?
- Hint: What are all the clones?
- So, make one state in M for each subset of Q