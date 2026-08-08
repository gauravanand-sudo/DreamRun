# DreamRun Roadmap — Weeks 19-24

## Week 19 — Benchmark methodology, compiler optimization and measurement hygiene
**Phase:** CPU, Memory & Performance Engineering  
**Dates:** 2026-12-14 to 2026-12-20  
**Read:** Fedor: performance measurements chapters. Compiler Explorer. Google Benchmark docs optional. Brendan Gregg measurement mindset.  
**Build / break / measure:** Create benchmark harness with warmup, repetitions, p50/p95/p99, anti-optimization safeguards. Demonstrate dead-code elimination, constant folding and noisy benchmarks.  
**Mastery gate:** Can defend benchmark methodology: workload, compiler flags, hardware, pinning, warmup, distributions and measurement error.  
**DSA:** Shortest paths  
**Video A:** Your C++ Benchmark Is Probably Lying  
**Video B:** I Built a Benchmark Harness That Catches Bad Measurements

## Week 20 — CPU pipeline, branch prediction, ILP and instruction cost
**Phase:** CPU, Memory & Performance Engineering  
**Dates:** 2026-12-21 to 2026-12-27  
**Read:** Fedor CPU architecture chapters. CS:APP machine-level programming sections. Intel optimization manual as reference, not cover-to-cover.  
**Build / break / measure:** Branch predictable/random datasets; branchy vs branchless; dependency chains vs independent operations. Inspect assembly and perf counters.  
**Mastery gate:** Explain pipeline stalls, dependency chains, branch mispredicts and why branchless can be worse. Tie claim to measurement.  
**DSA:** Trie  
**Video A:** One if Statement Made My C++ 5x Slower  
**Video B:** Branchy vs Branchless — Assembly and perf Tell the Truth

## Week 21 — Cache hierarchy, locality, cache lines, AoS vs SoA
**Phase:** CPU, Memory & Performance Engineering  
**Dates:** 2026-12-28 to 2027-01-03  
**Read:** Fedor memory architecture chapters. CS:APP memory hierarchy/cache sections.  
**Build / break / measure:** Measure sequential/random/strided access across working-set sizes. AoS vs SoA benchmark. Pointer-chasing vs contiguous traversal. Estimate cache boundaries from results.  
**Mastery gate:** Explain L1/L2/L3, cache lines, spatial/temporal locality, cache misses, prefetching and why linked structures hurt locality.  
**DSA:** Greedy  
**Video A:** I Measured L1, L2, L3 and RAM From C++  
**Video B:** AoS vs SoA: Your Data Layout Is an Algorithm

## Week 22 — Allocators, arenas, TLB, pages, NUMA and affinity
**Phase:** CPU, Memory & Performance Engineering  
**Dates:** 2027-01-04 to 2027-01-10  
**Read:** Fedor memory/performance chapters. Linux man pages mmap/madvise/sched_setaffinity. Brendan Gregg memory/NUMA reference.  
**Build / break / measure:** Benchmark new/delete vs preallocation/arena/pool. Measure page-touch behavior, working-set growth, thread affinity. Explore NUMA concept only if hardware supports it.  
**Mastery gate:** Explain page size, TLB, page faults, arenas, fragmentation, affinity and NUMA implications without claiming unsupported hardware results.  
**DSA:** Bit manipulation  
**Video A:** malloc in a Hot Path: How Bad Is It Really?  
**Video B:** I Built a Memory Arena and Measured Tail Latency

## Week 23 — Assembly literacy, vectorization/SIMD, compiler optimization, perf
**Phase:** CPU, Memory & Performance Engineering  
**Dates:** 2027-01-11 to 2027-01-17  
**Read:** CS:APP machine code. Fedor compiler optimization sections. Compiler Explorer. perf documentation/man pages.  
**Build / break / measure:** Read compiler output for loops/classes. Compare -O0/-O2/-O3/LTO. Trigger/disable vectorization; inspect reports. Use perf stat/record/report on prior benchmarks.  
**Mastery gate:** Can map hot source lines to assembly at a useful level; identify loads/stores/branches/vectorized loops and form optimization hypotheses.  
**DSA:** 1D DP  
**Video A:** You Don't Need to Be an Assembly Expert — But You Need This  
**Video B:** I Let the Compiler Vectorize My Loop, Then Proved It

## Week 24 — Latency distributions, tail latency and performance capstone
**Phase:** CPU, Memory & Performance Engineering  
**Dates:** 2027-01-18 to 2027-01-24  
**Read:** Fedor performance design chapters; Brendan Gregg latency methodology. Review all performance notes.  
**Build / break / measure:** Build latency harness with p50/p90/p99/p99.9 and histogram. Apply to thread pool/ring buffer/server microbenchmarks. Write formal benchmark report with limitations.  
**Mastery gate:** Performance mock >=80%. Never report only average. Can distinguish throughput/latency/tail; propose experiment before optimization.  
**DSA:** 2D DP  
**Video A:** Average Latency Is Hiding the Bug  
**Video B:** Optimizing p99.9 Without Guessing: Full C++ Performance Investigation
