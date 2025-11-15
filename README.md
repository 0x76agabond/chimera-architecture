# Chimera Architecture

A lightweight architectural experiment combining `Clean Architecture` with selective design patterns to increase flexibility and reduce boilerplate. 

---

## Abstract

`Chimera Architecture` is an extended version of  `Clean Architecture` with **higher flexibility** while keeping dependency rules intact. It **handles messy real-world data, complex object lifecycles, and reduces boilerplate** through composition-driven adapters.

---

## Motivation

I’ve been exploring modern software principles and noticed that many failures actually come from misusing features that were originally useful.

- Most security incidents begin with a **valid function being abused**.
- Some anti-patterns are basically **real patterns… just executed in the wrong context**.

So I wondered, **if misuse can flip good ideas into bad outcomes, maybe the reverse is also true**. 
What happens if I intentionally misuse anti-patterns to build an architecture?

---

## Real Motivation

Modern architectures like `Hexagonal` or `Clean Architecture` are great, but they come with real-world gaps:

- **They assume the environment is perfectly structured**

- **They generate a lot of boilerplate for simple tasks**

- **They struggle with legacy systems or messy long-lifecycle objects**.

`Chimera Architecture` is my attempt to address these gaps.
It mixes **multiple design patterns, OOP techniques, and architectural principles** on top of `Clean Architecture` (which is why I call it `Chimera`).

---

## Architecture

`Chimera Architecture` keeps **adapter**, **core**, and **presentation** behaving exactly as in original clean architecture.  
The extension comes from how **use cases** are decomposed into three internal components **application**, **service**, **kit**.

![Architecture](https://drive.google.com/uc?export=view&id=1i90STJxnKBzg38mWZEDMzxj8OiIMo3Ba)

---

#### adapter
`adapter` exposes infra capabilities in a normalized form.  
It contains no business logic, only bridges external systems into the application boundary.

#### core
`core` holds the pure use-case rules.  
It must remain deterministic, context-free, and independent from infra or presentation.

#### presentation
`presentation` interacts only with the application layer.  
It never touches business rules or infra details directly.

---

### Use Case Composition (Chimera Extension)

#### application
`application` is the orchestrator of a use case.  
It coordinates the order of operations between kit, core, and service.

#### service
`service` performs the real workflow steps.  
It interacts with adapters, executes procedural work, and provides the specific logic required by the use case.

#### kit
`kit` handles messy real-world data and irregular inputs.  
It cleans, normalizes, and prepares data before passing it to core or service.
