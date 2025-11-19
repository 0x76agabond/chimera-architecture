# Chimera Architecture – Pattern Overview

This directory lists the core patterns used across Chimera Architecture.  
Some are modified or intentionally misused to gain their strengths while mitigating their trade-offs.

Goal: **a practical, flexible, and robust architecture built on predictable patterns.**

---

## Patterns

1. **Executor** – Decorator × Composition  
   A central wrapper for logging, timing, error handling, and consistent `Result<T>` shaping.

2. **Template** – Template Method × Composition  
   Shared workflow skeleton for the 80% common flow, extensible via override or composition.

3. **3 Levels of DI** – static DI × context injection × type manipulation  
   Hybrid injection model combining container DI, runtime context, and safe type overrides.

4. **Use Cases** – Application × Service × Kit  
   Clean split: Application (flow), Service (work), Kit (data cleanup & normalization).

5. **Database** – Adapter × Dynamic SQL × Repository  
   Adapter handles raw infra, repository provides domain access, dynamic SQL gives flexibility.

6. **Adapter** – raw infra × Verifier  
   Raw infrastructure wrapped with a verifier to enforce boundary safety before execution.
