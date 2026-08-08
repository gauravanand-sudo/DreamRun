# DreamRun Roadmap — Weeks 31-36

## Week 31 — Low-latency measurement, clocks, CPU pinning and jitter
**Phase:** Low-Latency / HFT Engineering  
**Dates:** 2027-03-08 to 2027-03-14  
**Read:** Fedor performance/concurrency sections; man pages clock_gettime, sched_setaffinity. Read TSC concepts cautiously from architecture docs.  
**Build / break / measure:** Build latency timer utilities. Compare steady_clock/clock_gettime overhead; CPU affinity on/off; warm/cold runs. Document measurement limitations on one machine.  
**Mastery gate:** Explain latency vs jitter, p99.9, clock choice, affinity, frequency scaling concept, why cross-machine one-way latency is hard without clock sync.  
**DSA:** Random medium set A  
**Video A:** Nanoseconds Are Easy to Measure Wrong  
**Video B:** CPU Pinning: I Measured the p99.9 Difference

## Week 32 — Electronic-market mechanics for software engineers
**Phase:** Low-Latency / HFT Engineering  
**Dates:** 2027-03-15 to 2027-03-21  
**Read:** Read exchange/matching-engine primers from reputable exchange docs when needed; focus on engineering concepts: order types, price-time priority, market data vs order entry. No trading strategy study.  
**Build / break / measure:** Model order types and price-time priority. Design data schema for add/cancel/execute. Write invariants and deterministic matching tests.  
**Mastery gate:** Explain limit/marketable orders, book sides, price-time priority, partial fills, sequence numbers and why deterministic replay matters.  
**DSA:** Random medium set B  
**Video A:** How an Electronic Exchange Works — For C++ Engineers  
**Video B:** I Modeled Price-Time Priority Before Writing the Engine

## Week 33 — Feed handler: multicast, sequence gaps, parsing and zero-allocation paths
**Phase:** Low-Latency / HFT Engineering  
**Dates:** 2027-03-22 to 2027-03-28  
**Read:** Review UDP/multicast, data layout, allocation, endianness and cache topics. Read relevant Linux socket options/man pages.  
**Build / break / measure:** Build binary market-data publisher + feed handler. Preallocate buffers, parse messages, detect gaps, replay from file. Benchmark parser throughput and latency.  
**Mastery gate:** Explain feed-handler stages, sequence gaps, snapshot/recovery concept, allocations, parsing costs and cache-friendly schema.  
**DSA:** Random medium set C  
**Video A:** From UDP Packet to Order Book in Microseconds  
**Video B:** I Removed Every Heap Allocation From My Feed Handler

## Week 34 — Order book and matching engine data structures
**Phase:** Low-Latency / HFT Engineering  
**Dates:** 2027-03-29 to 2027-04-04  
**Read:** Review STL/cache locality. Study alternative representations: map/tree, flat arrays, indexed levels, intrusive lists conceptually.  
**Build / break / measure:** Build correct reference order book first; property/invariant tests. Then compare 2-3 data structures on synthetic distributions. Build matching engine with deterministic replay.  
**Mastery gate:** Choose structure based on price range/workload. Explain correctness invariants, cancellation lookup, FIFO at price level and cache trade-offs.  
**DSA:** Random medium set D  
**Video A:** What Data Structure Should an HFT Order Book Use?  
**Video B:** I Built Three Order Books and Benchmarked Them

## Week 35 — Order gateway, risk checks, memory pools and latency instrumentation
**Phase:** Low-Latency / HFT Engineering  
**Dates:** 2027-04-05 to 2027-04-11  
**Read:** Review allocators, ring buffers, networking, error handling and architecture. Read only engineering-level risk concepts.  
**Build / break / measure:** Build order gateway with validation, simple limits, object pool, SPSC handoff and latency stamps. Add histogram and structured metrics.  
**Mastery gate:** Explain where to put checks, how to avoid undefined behavior while optimizing, how to preserve observability without destroying hot-path latency.  
**DSA:** Random medium set E  
**Video A:** The Fastest Code Is Useless If Risk Checks Are Wrong  
**Video B:** Building a Low-Latency Order Gateway With Zero Hot-Path Allocation

## Week 36 — HFT capstone: CppValley Exchange optimization and mock
**Phase:** Low-Latency / HFT Engineering  
**Dates:** 2027-04-12 to 2027-04-18  
**Read:** Review Fedor + concurrency + Linux + network notes. Current target-role descriptions for low-latency systems as competency checklist.  
**Build / break / measure:** Integrate feed -> order book -> strategy stub -> gateway -> matching engine. Profile end-to-end. Produce benchmark methodology, flame/perf evidence, p50/p99/p99.9 and architecture README.  
**Mastery gate:** 90-minute HFT systems mock. Must defend every optimization with evidence and every lock-free/data-layout choice with invariants.  
**DSA:** Timed medium review  
**Video A:** Where Did My Trading Engine Lose Its Microseconds?  
**Video B:** Full HFT C++ Mock Interview: Cache, Atomics, Linux, Networking
