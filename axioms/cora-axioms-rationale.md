# CORA Axioms — Rationale
Why CORA requires exactly these three axioms — no more and no less.

CORA is defined by three minimal axioms:

1. **Capability is the only authority.**  
2. **All interaction occurs only through message passing.**  
3. **Capabilities transfer only by explicit message.**

This document explains why each axiom is necessary, why none can be removed,
and why together they form a complete and minimal foundation for the CORA model.

---

## Axiom 1 — Capability is the Only Authority

### Why this axiom is necessary
If authority can come from sources other than capabilities — such as
process identity, global variables, ambient privileges, inherited handles,
or implicit OS context — then authority becomes:

- non-local  
- unpredictable  
- difficult to audit  
- vulnerable to accidental leaks  

By defining *all* authority as capabilities, CORA enables:

- **local reasoning** — a task’s authority = the capabilities it holds  
- **predictability** — no hidden power  
- **uniformity** — all resources and actions reduced to one primitive  
- **least authority by construction**  

### Why it cannot be removed
Without this axiom, capabilities lose meaning because ambient privilege would still exist.

### Why it cannot be merged with the other axioms
Axiom 1 answers: **What is authority?**  
Axiom 2 and 3 answer: **How authority is used and moved?**  
Completely different dimensions.

---

## Axiom 2 — All Interaction Occurs Only via Message Passing

### Why this axiom is necessary
If objects can affect one another without message passing — via shared memory,
global namespaces, implicit I/O, or hidden side effects — then:

- capabilities no longer define all possible effects  
- authority flow becomes ambiguous  
- isolation breaks  
- distributed and local semantics diverge  

Restricting all interaction to explicit messages provides:

- **traceability** — every effect has a causal message  
- **isolation** — no message = no interaction  
- **distributed-ready semantics** — local ≡ remote  
- **deterministic reasoning** — effects form a message graph  

### Why it cannot be removed
Removing this axiom collapses CORA into a traditional OS with unpredictable side effects.

### Why it cannot be merged with Axiom 1
Axiom 1 defines *who may act*;  
Axiom 2 defines *how actions occur*.  
Both are needed independently.

---

## Axiom 3 — Capabilities Transfer Only by Explicit Message

### Why this axiom is necessary
If capabilities can move implicitly — through forking, global tables, shared pages,
inheritance, or runtime auto-propagation — then:

- authority leaks become inevitable  
- capability ownership cannot be audited  
- least authority cannot be enforced  
- formal verification becomes impossible  

By requiring explicit transfer, CORA ensures:

- **auditability of authority flow**  
- **no accidental leakage**  
- **true encapsulation**  
- **predictable, controllable capability ownership**  

### Why it cannot be removed
Implicit transfer destroys the core property of capability systems:
control over authority propagation.

### Why it cannot be merged with Axiom 2
Axiom 2 governs *effects*;  
Axiom 3 governs *authority movement*.  
Message passing ≠ capability passing — these must be distinct rules.

---

## Why exactly these three axioms?

These axioms answer three orthogonal questions:

| Fundamental Question | Corresponding Axiom |
|----------------------|---------------------|
| **What is authority?** | Axiom 1 |
| **How do objects interact?** | Axiom 2 |
| **How does authority flow?** | Axiom 3 |

Together they form a **closed minimal set**:

- Removing any axiom → incomplete model  
- Merging any axioms → loss of clarity, broken semantics  
- Adding extra axioms → unnecessary complexity, violates minimality  

This is the simplest possible model that still maintains:

- security  
- isolation  
- composability  
- distributed consistency  
- formal provability  

---

## High-Level Consequences (Not Axioms)
From these three axioms, CORA immediately gains:

- no ambient authority  
- no implicit sharing  
- perfect default isolation  
- auditable authority graph  
- local and distributed semantics unify  
- capability flow becomes mathematically analyzable  

These will be expanded in `cora-axioms-implications.md`.

---

## Conclusion

CORA has exactly three axioms because:

- each axiom is essential  
- each defines a distinct dimension of authority  
- together they completely describe the runtime’s semantics  
- the set is minimal, self-contained, and closed  

This is the philosophical and mathematical foundation of CORA.
