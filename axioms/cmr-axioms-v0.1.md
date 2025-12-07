# CMR Axioms v0.1  
Capability Message Runtime — Formal Axioms

CMR is a minimal, capability-based, message-only runtime system.
Its entire behavioral universe is defined by **three axioms**.

---

## **Axiom 1 — Authority derives only from capabilities**

A capability is the *sole* representation of authority in CMR.
If a task does not hold a capability, it cannot perform the corresponding action.

- No global privileges  
- No ambient authority  
- No inherited rights  
- No "superuser" exceptions  

Possession = permission.

---

## **Axiom 2 — All communication occurs only via messages**

Tasks cannot interact by shared memory, global variables, or hidden channels.  
Every form of communication — data, signals, capabilities — is transmitted explicitly by messages.

Message channels are the only mechanism of interaction in CMR.

This ensures:

- Isolation  
- Deterministic reasoning  
- Formal verifiability  
- Auditable authority flows  

---

## **Axiom 3 — Capabilities transfer only via explicit messages**

A capability may not be duplicated, leaked, or implicitly inherited.
It transfers from one task to another **only** if explicitly attached to a message.

This guarantees:

- Transparent authority flow  
- No hidden capability creation  
- Trackable and auditable delegation  
- Minimal TCB impact  

---

# **Interpretation**

These three axioms fully define:

- The security model  
- The authority model  
- The messaging semantics  
- The runtime constraints  
- The TCB boundaries  

All specifications and implementations of CMR **must be consistent with these axioms**.

This document represents the normative foundation for the upcoming CMR RFC.
