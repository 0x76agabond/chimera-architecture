# **Chimera Architecture – Pattern Overview**

This directory lists the core patterns used across Chimera Architecture.  
Some are modified or intentionally misused to gain their strengths while mitigating their trade-offs.

## **Goal**
**A practical, flexible, and robust architecture built on predictable patterns.**

---

## **Real Goal**
- A set of `Architectural Patterns` that developers can mix with `Clean Architecture`  
to safely improve flexibility while keeping the core principles.  
- An architectural structure that can **scale according to project complexity**,
remaining simple for small systems and progressively structured for larger ones.

---

## **Menu**

1. **Helloworld**  
   An introduction to the fundamental rules and mindset behind Chimera.

2. **Use Cases** – **Flow × Service × Kit**  
   Clean split: Flow (Orchestrator), Service (work), Kit (data cleanup & normalization).

3. **Executor** – **Decorator × Composition**  
   A central wrapper for logging, timing, error handling, and consistent `Result<T>` shaping.

4. **Template** – **Template Method × Composition**  
   Shared workflow skeleton for the 80% common flow, extended through override or composition.

5. **3 Levels of DI** – **Static DI × Context Injection × Type Manipulation**  
   Hybrid injection model combining container DI, runtime context, and safe runtime type overrides.

6. **Database** – **Adapter × Dynamic Query × Repository**  
   Adapter handles raw infra, Repository provides domain access, Dynamic Query gives flexibility.

7. **Adapter** – **Raw Infra × Verifier**  
   Low-level infrastructure wrapped with a Verifier to enforce boundary safety before execution.

8. **Meta Programing** - **Reflection x Caching**.  
   Controlled use of reflection combined with caching to enable flexibility without significant performance costs.

9. **Authorization** – **Reflection × DDD**  
   Auto-authorization based on namespace/domain rules, no more attributes required.

10. **Vision** – **Log × Architecture × AI**  
   AI as developer, reviewer, onboarding assistant, and boilerplate generator.
