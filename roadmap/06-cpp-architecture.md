# DreamRun Roadmap — Weeks 37-42

## Week 37 — Design principles: coupling, cohesion, SoC, dependency inversion
**Phase:** C++ Architecture & Staff-Level Design  
**Dates:** 2027-04-19 to 2027-04-25  
**Read:** Iglberger opening design/principles chapters: dependencies, abstractions, testability, SOLID in context. Core Guidelines interfaces.  
**Build / break / measure:** Take messy module from prior capstone and draw dependency graph. Refactor one high-coupling path. Write ADR for options and consequences.  
**Mastery gate:** Explain design in terms of dependencies/changeability/testability, not pattern names. Identify accidental coupling.  
**DSA:** NeetCode 150: arrays/hash  
**Video A:** Good C++ Design Is Dependency Management  
**Video B:** I Refactored a Working System Without Rewriting It

## Week 38 — Strategy/Command, composition and value semantics
**Phase:** C++ Architecture & Staff-Level Design  
**Dates:** 2027-04-26 to 2027-05-02  
**Read:** Iglberger Strategy/Command/value-semantics sections. cppreference variant/function where used.  
**Build / break / measure:** Implement runtime inheritance, std::function, templates/policies and type-erased strategy for same behavior. Compare compile/runtime costs and testability.  
**Mastery gate:** Choose dynamic/static/value-semantic strategy deliberately. Explain ABI, code size, extensibility and testability trade-offs.  
**DSA:** NeetCode 150: two-pointer/window  
**Video A:** Strategy Pattern: Four Modern C++ Implementations  
**Video B:** I Benchmarked Runtime vs Compile-Time Polymorphism

## Week 39 — Observer, Adapter, Bridge and boundary design
**Phase:** C++ Architecture & Staff-Level Design  
**Dates:** 2027-05-03 to 2027-05-09  
**Read:** Iglberger Observer/Adapter/Bridge sections. Core Guidelines interface boundaries.  
**Build / break / measure:** Add metrics/event observers to exchange/KV without coupling core. Wrap external-style interface with adapter. Use Bridge/PImpl where binary boundary matters.  
**Mastery gate:** Explain event ownership/lifetime, observer invalidation, adapter intent, Bridge vs Strategy and dependency direction.  
**DSA:** NeetCode 150: stack/binary search  
**Video A:** Observer Pattern: The Lifetime Bug Nobody Mentions  
**Video B:** Adapting a Legacy C++ API Without Infecting the Codebase

## Week 40 — CRTP, static polymorphism, type erasure, PImpl and ABI stability
**Phase:** C++ Architecture & Staff-Level Design  
**Dates:** 2027-05-10 to 2027-05-16  
**Read:** Iglberger CRTP/type-erasure/Bridge/PImpl-related sections. Revisit ABI week.  
**Build / break / measure:** Build equivalent plugin interface with virtual, CRTP and type erasure. Build PImpl library and demonstrate implementation change without public-layout change.  
**Mastery gate:** Explain when templates leak implementation/ABI, code bloat concept, type-erasure mechanics, CRTP limits and PImpl costs.  
**DSA:** NeetCode 150: trees  
**Video A:** Virtual vs CRTP vs Type Erasure: Pick the Right Polymorphism  
**Video B:** I Changed a Library Internals Without Breaking Its ABI

## Week 41 — API design, error handling, versioning, testing and observability
**Phase:** C++ Architecture & Staff-Level Design  
**Dates:** 2027-05-17 to 2027-05-23  
**Read:** Core Guidelines error handling/API sections; Iglberger testability principles. cppreference expected if available in chosen standard.  
**Build / break / measure:** Design public API for KV/exchange module. Compare exceptions/error codes/expected-style result. Add structured logs, metrics and fault injection.  
**Mastery gate:** Defend error model and API compatibility. Explain exception safety at boundaries, versioning strategy and test seams.  
**DSA:** NeetCode 150: graphs  
**Video A:** Exceptions vs Error Codes vs expected: Architect-Level Trade-offs  
**Video B:** I Designed a C++ API to Survive Five Years of Change

## Week 42 — Architecture capstone + Staff technical leadership stories
**Phase:** C++ Architecture & Staff-Level Design  
**Dates:** 2027-05-24 to 2027-05-30  
**Read:** Review Iglberger and your ADRs. Use Google current Staff role expectations as leadership checklist: architecture, outcomes, influence, technical direction.  
**Build / break / measure:** Produce architecture doc for one capstone: context, requirements, constraints, alternatives, diagrams, APIs, failure modes, test plan, performance plan, evolution. Build 12 Staff stories.  
**Mastery gate:** 2-hour architecture review: defend alternatives and rejected options. Have 12 STAR/CARL-style technical leadership stories with sanitized employer details.  
**DSA:** NeetCode 150: DP  
**Video A:** How a Staff Engineer Writes an Architecture Decision  
**Video B:** Full C++ Architect Interview: Design, Trade-offs, Evolution
