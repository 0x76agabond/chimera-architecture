# **Chimera Architecture**
A lightweight architectural experiment combining `Clean Architecture` with selective design patterns to increase flexibility and reduce boilerplate. 

---

## **Abstract**

`Chimera Architecture` is an extended version of  `Clean Architecture` with **higher flexibility** while keeping dependency rules intact. It **handles messy real-world data, complex object lifecycles, and reduces boilerplate** through composition-driven adapters.

---

## **Motivation**

I’ve been exploring modern software principles and noticed that many failures actually come from misusing features that were originally useful.

- Most security incidents begin with a **valid function being abused**.
- Some anti-patterns are basically **real patterns… just executed in the wrong context**.

So I wondered, **if misuse can flip good ideas into bad outcomes, maybe the reverse is also true**. 
What happens if I intentionally misuse anti-patterns to build an architecture?

---

## **Real Motivation**

Modern architectures like `Hexagonal` or `Clean Architecture` are great, but they come with real-world gaps:

- **They assume the environment is perfectly structured**

- **They generate a lot of boilerplate for simple tasks**

- **They struggle with legacy systems or messy long-lifecycle objects**.

`Chimera Architecture` is my attempt to address these gaps.
It mixes **multiple design patterns, OOP techniques, and architectural principles** on top of `Clean Architecture` (which is why I call it `Chimera`).

---

## **Architecture**

`Chimera Architecture` keeps **adapter**, **core**, and **presentation** behaving exactly as in original clean architecture.  
The extension comes from how **use cases** are decomposed into three internal components **application**, **service**, **kit**.

![Architecture](https://drive.google.com/uc?export=view&id=1i90STJxnKBzg38mWZEDMzxj8OiIMo3Ba)

---

### Adapter
`Adapter` exposes infra capabilities in a normalized form.  
It contains no business logic, only bridges external systems into the `Use cases` boundary.

### Core
`Core` holds the pure use-case rules.  
It must remain deterministic, context-free, and independent from infra or presentation.

### Presentation
`Presentation` interacts only with the `Use cases` layer.  
It never touches business rules or infra details directly.

### Use Cases (Chimera Extension)

#### Application
`Application` is the orchestrator of a use case.  
It coordinates the order of operations between kit, core, and service.

#### Service
`Service` performs the real workflow steps.  
It interacts with `Adapter Interface`, executes procedural work, and provides the specific logic required by the use case.

#### Kit
`Kit` handles messy real-world data and irregular inputs.  
It cleans, normalizes, and prepares data before passing it to core or service.

--- 

## **Rules**

1. Must follow **Clean Architecture** dependency rule.  
2. `Adapter` must pair with a `Verifier` or `Repository`.  
3. `Adapter` exposes **everything** the underlying library/infra can do.  
4. `Verifier`/`Repository` stays **stateless** and validates all input before calling the adapter.  
5. `Application` orchestrates the full use-case flow.  
6. `Service` provides use-case–specific logic.  
7. `Kit` handles real-world messy data and external chaos.  
8. `Executor` is the **single decorator** for logging, timing, and exception capture.  

9. There are **3 levels of dependency injection**:  
   - Static dependencies via **DI container**.  
   - Runtime context injected via **Init()**.  
   - Runtime types injected via **inheritance or factory**.  

10. All layers use **composition first**, inheritance second, and marker interfaces to lock behavior contracts + enable DI wiring.  
11. **Template Method** defines shared boilerplate and allows subclasses to override specific steps.  
12. `EnsureInit()` blocks execution until all required context is ready.  

13. Each use-case expands **only as needed**:  
    - Simple flows → only `Application` (**pure Clean Architecture**).  
    - Medium flows → + `Service`.  
    - Heavy flows → + `Kit` to isolate external chaos.  
    - Data-driven flows → + `Repository`.  

14. No logic inside **Adapter**; no infra inside **Service**; no business inside **Repository**.  
15. Boundaries must **never leak** — data crosses layers only via DTO/VO.  
16. No global state — all state must live inside controlled runtime context.  
17. The system grows or shrinks with complexity, but **boundaries stay clean and stable**.

---

## **Real Real Motivation**

`Chimera Architecture` was designed to push `Clean Architecture` toward higher **flexibility** while keeping the **dependency rule** fully intact.  
Its core idea is simple — every layer follows the same lifecycle pattern, allowing messy real-world data and complex object flows to be handled without breaking boundaries.

A key property of `Chimera Architecture` is the **structural rhythm inside each file type**:

- `Application` – only orchestration.  
- `Service` – only **small, minimal business logic**.  
- `Kit` – only **data cleanup, normalization, and transformation**.  

Because each layer keeps a single, predictable responsibility, the entire architecture forms a stable pattern with **low boilerplate** and **clear separation**.  

### AI as a Natural Assistant

This consistency makes the architecture deeply **AI-friendly**:

- AI knows the theoretical structure better than a typical senior (***me**).  
- AI is **consistent** and follows rules without ego.  
- AI can correct misuse of layers and maintain structural purity.  
- AI can help onboard new team member by “fighting” them all day until the logic makes sense.  
- AI can generate boilerplate and enforce boundaries reliably.

As a result, `Chimera Architecture` becomes a **repeatable ecosystem** where:

- Senior developers set direction.  
- Juniors learn faster through consistent patterns
- AI acts as a tireless reviewer, coach, and collaborator.

Humans and AI can iterate, refine, and expand the system with clarity.

---

## **Benefits**

- **Extremely flexible**, because each use-case can scale up or down depending on business complexity.  
- **Three levels of injection** allow Chimera Architecture to handle runtime objects (e.g., WebView2) and even transform behavior on demand — while still respecting dependency rules.  
- **Composition × Template Method × Marker Interface** reduces boilerplate but still respects dependency inversion.  
- In cases where multiple `entity` share similar columns, the reduction in **boilerplate** becomes highly significant.
- Each use-case component becomes **truly SRP**.  
  At scale, this produces a natural effect where each file type shares a consistent structure.  
- This structural similarity makes it **AI-friendly**, enabling AI to become an onboarding assistant or even a boilerplate generator.

## **Real Real Real Motivation**
*I did all these things because I'm too lazy to copy-paste boilerplate and I'm unemployed. Poor me.*

## **Conclusion**
- `Chimera Architecture` is an extended version of `Clean Architecture` with higher flexibility and lower boilerplate.
- The idea of **“misusing anti-patterns”** means **leveraging strong patterns that normally carry high trade-offs, but implementing them in a controlled way so the risk becomes acceptable or even beneficial**.
- `Clean Architecture` is already inherently **AI-friendly**, so any architecture built on top of it becomes naturally compatible with AI reasoning.
- Reduced boilerplate means fewer tokens and smaller class context, which increases the chance that an AI assistant can fully understand, manipulate, and refactor the file without losing context.