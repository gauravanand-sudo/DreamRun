# DreamRun

**Mission:** From Staff C++ engineer to interview-ready **HFT / Google Infrastructure / C++ Architect / GPU-AI Infrastructure** candidate through deep practical mastery.

**Run:** 2026-08-10 to 2027-11-07 — **65 weeks**  
**Publishing:** maximum **2 CppValley videos/week**  
**Mastery rule:** never advance by hiding a failed gate. Repeat the weak lab/concept and mark the week `↻`.

> Assumption: the two system-design volumes you mentioned are **Alex Xu, System Design Interview Vol. 1 & 2**. If you meant another author, replace that resource in the tracker.

## Non-negotiable learning loop

1. Read the primary source.
2. Close the source and reconstruct the mental model.
3. Implement a minimal experiment.
4. Deliberately break it.
5. Debug it with the appropriate tool.
6. Benchmark/profile where performance is relevant.
7. Write invariants, trade-offs, and failure cases.
8. Answer interview questions aloud without notes.
9. Pass the mastery gate.
10. Only then record the CppValley explanation.

**Recording is the exam, not the study session.**

## Weekly time budget

| Day | Minutes | Default work |
|---|---:|---|
| Monday | 120 | Recall + DSA new + primary reading + questions |
| Tuesday | 120 | Recall + DSA review + implementation + commit |
| Wednesday | 135 | DSA new + debug/inspect + Video A hook + publish previous A |
| Thursday | 120 | DSA review + benchmark/profile + interview answers |
| Friday | 90 | DSA new + closed-book mastery quiz + Video B storyboard |
| Saturday | 270 | Deep lab/capstone + record/edit Video A + repo cleanup |
| Sunday | 210 | Deep lab + record/edit Video B + publish previous B + retrospective |

Total planned core work: **~17.75 hours/week**. MTech classes/assignments are outside this budget.

## Phase map

| Weeks | Phase | Outcome |
|---:|---|---|
| 1-10 | C++ Language & Toolchain | C++ interview-level command |
| 11-18 | Concurrency & Memory Model | Practical correctness + atomics reasoning |
| 19-24 | CPU/Memory/Performance | Evidence-based optimization |
| 25-30 | Linux & Networking | Real systems programming |
| 31-36 | Low-Latency/HFT | Exchange engineering capstone |
| 37-42 | C++ Architecture | Architect/Staff trade-off thinking |
| 43-48 | Distributed Systems | Google-style infrastructure design |
| 49-54 | CUDA/GPU | GPU programming + profiling |
| 55-59 | AI Inference Systems | Transformers/inference from systems perspective |
| 60 | Integrated Capstone | C++/CUDA inference proof |
| 61-65 | Interview Bootcamp | Convert knowledge into offers |

## Four public capstones

- `projects/cppvalley-runtime` — queues, thread pool, allocators, concurrency/perf benchmarks.
- `projects/cppvalley-kv` — epoll server, binary protocol, persistence, replication/sharding experiments.
- `projects/cppvalley-exchange` — market-data feed, order book, matching engine, gateway, latency instrumentation.
- `projects/cppvalley-inference` — CPU/CUDA ops, attention/KV cache, scheduler/inference experiments.

## CppValley video contract

Every serious video follows:

**Hook (surprising failure/result) -> Mental model -> Minimal code -> Break it -> Measure/profile -> Fix -> Limitations -> Interview Mode**

Do not publish a performance claim without:
- workload,
- compiler + flags,
- machine/OS,
- iteration/warmup details,
- relevant percentiles,
- raw/reproducible code,
- limitations.

## DSA retention system

Use **Striver selectively for concept rebuild**, then **NeetCode 150** for pattern practice.

Weekly default:
- Monday: new problem
- Tuesday: spaced review
- Wednesday: new problem
- Thursday: spaced review
- Friday: new problem
- Weekend: only a timed mock when scheduled

Review each important problem/pattern at approximately:
**D+2, D+7, D+21, D+60, D+120**.

A solved problem does not count as retained until you can:
1. identify the pattern without being told,
2. explain brute force and optimized approach,
3. code it under time,
4. test edge cases,
5. explain complexity.

## Staff/Architect story journal

Maintain 12 sanitized stories:
architecture ownership, hard bug, performance improvement, disagreement, failure, ambiguity, cross-team influence, mentoring, technical debt, reliability, trade-off, incident/debugging.

Never put Synopsys confidential code, architecture, screenshots, datasets, benchmarks, or internal details into this repository or CppValley.

## Tracker

Place `DreamRun_15_Month_Master_Tracker.xlsx` under `tracker/`. It contains:
- dashboard,
- all 65 weeks,
- daily 7-day tracker,
- 130-video pipeline,
- DSA spaced-repetition sheet,
- target-role matrix,
- resources,
- repo map.
