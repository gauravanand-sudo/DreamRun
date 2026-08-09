# DreamRun

DreamRun is a **mastery-first engineering curriculum** for becoming exceptional at modern C++, systems programming, low-latency engineering, C++ architecture, distributed infrastructure, GPU/CUDA, and AI inference systems.

There is **no fixed video quota** and no artificial rule that a topic must fit into one week. A topic is complete only when it can be explained, implemented, broken, debugged, measured, and defended in an interview without notes.

## Canonical documents

- [`MASTER_PLAN.md`](MASTER_PLAN.md) — the only overall DreamRun plan.
- [`curriculum/01-cpp-mastery.md`](curriculum/01-cpp-mastery.md) — the current curriculum. It starts with all 42 Effective Modern C++ items and then extends into modern C++17/20/23.
- [`templates/mastery-unit.md`](templates/mastery-unit.md) — checklist for every concept.
- [`templates/video.md`](templates/video.md) — CppValley video extraction template.
- [`templates/benchmark.md`](templates/benchmark.md) — reproducible performance-work template.
- [`templates/interview-card.md`](templates/interview-card.md) — interview-revision template.

## Current priority

**C++ mastery comes first.** Do not rush into HFT, distributed systems, CUDA, or AI just to satisfy a calendar. Those domains are downstream of the C++/systems foundation and will be expanded only when the prerequisite mastery gates are passed.

## The DreamRun rule

For each concept:

1. Read the primary source.
2. Reconstruct the mental model closed-book.
3. Enumerate edge cases and interview traps.
4. Implement minimal experiments.
5. Deliberately break the code.
6. Debug with the appropriate tools.
7. Inspect compiler/runtime behavior where relevant.
8. Benchmark/profile where relevant.
9. Answer interview questions aloud.
10. Pass a closed-book mastery gate.
11. Only then decide how many CppValley videos the concept deserves.

**Videos are outputs of mastery, not constraints on mastery.** One topic may produce one video; another may produce ten.

## Content standard

CppValley videos should usually follow:

**Hook → mental model → minimal code → failure/broken case → evidence → fix → trade-offs → interview mode**

Performance claims must include the machine/software environment, workload, compiler and flags, measurement method, relevant distributions/percentiles, and limitations.

## DSA

DSA runs in parallel because retention requires repetition. Use a pattern-oriented path and spaced retrieval instead of repeatedly completing large courses.

Suggested review rhythm for important problems/patterns: **D+2 → D+7 → D+21 → D+60 → D+120**.

## Repository hygiene

This repository should contain only current DreamRun material. Superseded roadmaps are deleted instead of kept beside the new plan.

Never publish employer-confidential code, architecture, screenshots, data, benchmarks, or proprietary information.