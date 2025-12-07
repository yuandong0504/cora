# Rationale for the CMR Axioms  
Why these three axioms — and why only these three?

CMR's design principles were not chosen for convenience.  
They were chosen because they uniquely satisfy four goals:

- **Minimality**  
- **Security & Isolation**  
- **Explainability**  
- **RFC suitability**

Below是每条公理存在的理由。

---

# **1. Why “Authority derives only from capabilities”?**

Because any other source of authority creates ambiguity:

- user identity  
- global privileges  
- inherited rights  
- ambient power (e.g., POSIX uid/gid)  
- implicit access from context  

These models are the root cause of:

- privilege escalation  
- confused deputy attacks  
- ambient authority abuse  

Capabilities eliminate all of these by replacing *implicit* authority with *explicit possession*.

---

# **2. Why “All communication occurs only via messages”?**

Shared memory → race conditions, data leakage, aliasing  
Signals → implicit channels  
Global state → unpredictable behavior

Messages are:

- explicit  
- traceable  
- inspectable  
- formalizable  
- secure  
- schedulable  

A message-only world is the simplest universe where task interaction remains **fully auditable**.

This is essential for both reasoning and RFC standardization.

---

# **3. Why “Capabilities transfer only via explicit messages”?**

If capabilities could be duplicated or leaked implicitly:

- authority becomes untrackable  
- delegation becomes invisible  
- TCB expands  
- formal analysis collapses  

Explicit transfer guarantees:

- transparent authority graph  
- deterministic audit trail  
- zero hidden delegation  
- extremely small TCB  

This is the cornerstone of formal verification.

---

# **4. Why exactly three axioms?**

Because:

- They are **mutually independent**  
- They are **collectively sufficient**  
- They reduce CMR to the smallest possible definable universe  

Adding more axioms → redundancy  
Removing any → system becomes incomplete或不安全

Three is the minimal complete set.

---

# **Conclusion**

CMR is built on the smallest axiom set capable of defining:

- a secure runtime  
- a message-based universe  
- a capability authority graph  
- an auditable interaction model  
- a verifiable TCB boundary  

This rationale document exists to justify these choices for standardization and RFC evaluation.
