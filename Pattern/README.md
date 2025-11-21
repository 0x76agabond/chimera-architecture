# **Chimera Architecture – Pattern Overview**

This directory lists the core patterns used across Chimera Architecture.  
Some are modified or intentionally misused to gain their strengths while mitigating their trade-offs.

## **Goal**
**A practical, flexible, and robust architecture built on predictable patterns.**

---

## **Real Goal**
A set of `Architectural Patterns` that developers can mix with `Clean Architecture`  
to safely improve flexibility while keeping the core principles intact.

---

## **Patterns**

1. **Executor** – **Decorator × Composition**  
   A central wrapper for logging, timing, error handling, and consistent `Result<T>` shaping.

2. **Template** – **Template Method × Composition**  
   Shared workflow skeleton for the 80% common flow, extended through override or composition.

3. **3 Levels of DI** – **Static DI × Context Injection × Type Manipulation**  
   Hybrid injection model combining container DI, runtime context, and safe runtime type overrides.

4. **Use Cases** – **Flow × Service × Kit**  
   Clean split: Flow (Orchestrator), Service (work), Kit (data cleanup & normalization).

5. **Database** – **Adapter × Dynamic SQL × Repository**  
   Adapter handles raw infra, Repository provides domain access, Dynamic SQL gives flexibility.

6. **Adapter** – **Raw Infra × Verifier**  
   Low-level infrastructure wrapped with a Verifier to enforce boundary safety before execution.

7. **Authorization** – **Reflection × DDD × Cache**  
   Auto-authorization based on namespace/domain rules — no more attributes required.

8. **Vision** – **Log × Architecture × AI**  
   AI as developer, reviewer, onboarding assistant, and boilerplate generator.
