# DreamRun Roadmap — Weeks 11-18

## Week 11 — Thread lifecycle, ownership, joining, exceptions, task decomposition
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-10-19 to 2026-10-25  
**Read:** Anthony Williams: introductory chapters on concurrency and managing threads. cppreference std::thread/jthread/stop_token.  
**Build / break / measure:** Write thread lifecycle labs: join, detach hazards, RAII thread wrapper, jthread cancellation. Parallelize CPU work with partitioning; measure overhead vs work size.  
**Mastery gate:** Explain thread ownership, joinability, cancellation, exception propagation and when parallelism loses to overhead.  
**DSA:** Binary trees traversals  
**Video A:** std::thread: What Actually Happens When You Create a Thread?  
**Video B:** 1 vs 2 vs 4 vs 8 vs 16 Threads — Where Scaling Stops

## Week 12 — Mutexes, lock types, deadlock, contention
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-10-26 to 2026-11-01  
**Read:** Anthony Williams: sharing data and mutexes. cppreference mutex, lock_guard, unique_lock, scoped_lock, shared_mutex.  
**Build / break / measure:** Create race, fix with mutex. Create 5 deadlocks; fix using ordering/scoped_lock. Measure critical-section contention. Implement guarded object abstraction.  
**Mastery gate:** Explain lock granularity, lock ordering, recursive_mutex smell, shared_mutex trade-offs, convoying concept. Diagnose deadlock from thread backtrace.  
**DSA:** BST  
**Video A:** Mutex Internals: What Are You Really Protecting?  
**Video B:** I Created Five Deadlocks on Purpose

## Week 13 — Condition variables, semaphores, latches/barriers, futures/promises
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-11-02 to 2026-11-08  
**Read:** Anthony Williams synchronization chapters. cppreference condition_variable, semaphore, latch, barrier, future, promise, async.  
**Build / break / measure:** Implement bounded producer-consumer queue with CV predicate and shutdown. Compare CV vs semaphore where appropriate. Implement promise/future error propagation and barrier-based stage.  
**Mastery gate:** Explain spurious wakeups, lost wakeup misconception, predicates, future lifecycle, async launch policies. Write correct bounded queue from memory.  
**DSA:** Heap/priority queue  
**Video A:** Condition Variables Without Memorizing the API  
**Video B:** Building a Bounded Producer-Consumer Queue From Scratch

## Week 14 — Thread-safe interface design and blocking data structures
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-11-09 to 2026-11-15  
**Read:** Anthony Williams chapters on designing concurrent code and thread-safe data structures.  
**Build / break / measure:** Build ThreadSafeQueue, ThreadSafeStack (then critique it), blocking queue and concurrent cache wrapper. Write race-focused tests and cancellation/shutdown semantics.  
**Mastery gate:** Explain why interface design can make individually locked methods unsafe. Identify compound-operation races and define invariants.  
**DSA:** Tree recursion patterns  
**Video A:** Why a Thread-Safe Class Can Still Be Unsafe  
**Video B:** Designing a Concurrent Queue You Can Actually Shut Down

## Week 15 — C++ memory model, data races, happens-before
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-11-16 to 2026-11-22  
**Read:** Anthony Williams memory model chapter. cppreference memory model, data races, happens-before, synchronization. Optional memory-model article.  
**Build / break / measure:** Create message-passing litmus tests; distinguish non-atomic data race from atomic ordering. Draw event graphs for 20 examples. Use ThreadSanitizer for actual races.  
**Mastery gate:** Explain sequenced-before, synchronizes-with, happens-before and data race in C++ abstract-machine terms without relying on 'CPU probably does X'.  
**DSA:** Graphs BFS/DFS  
**Video A:** The C++ Memory Model From First Principles  
**Video B:** I Drew 20 Happens-Before Graphs Until Atomics Made Sense

## Week 16 — Atomics, CAS and memory orderings
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-11-23 to 2026-11-29  
**Read:** Anthony Williams atomic operations. cppreference std::atomic, compare_exchange, memory_order. Fedor concurrency chapters selectively.  
**Build / break / measure:** Implement counters with mutex/atomic/sharding. Build acquire-release message passing, relaxed counters, CAS loop. Benchmark and inspect x86 assembly; note portability.  
**Mastery gate:** Explain relaxed/acquire/release/acq_rel/seq_cst, CAS weak vs strong, failure ordering and what each guarantees.  
**DSA:** Topological sort  
**Video A:** std::atomic Is NOT Just a Faster Mutex  
**Video B:** Relaxed vs Acquire/Release vs SeqCst — Code, Assembly, Benchmark

## Week 17 — Lock-free structures, SPSC ring buffer, ABA and reclamation concepts
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-11-30 to 2026-12-06  
**Read:** Anthony Williams lock-free data-structure chapters. Fedor concurrent structures. cppreference atomics.  
**Build / break / measure:** Build mutex queue baseline, then SPSC ring buffer with atomics. Explore lock-free stack educationally and demonstrate ABA concept; document why memory reclamation is hard.  
**Mastery gate:** Define lock-free/wait-free/obstruction-free. Explain ABA, reclamation options conceptually, SPSC invariants and why lock-free can be slower.  
**DSA:** Union-Find / DSU  
**Video A:** Lock-Free Does NOT Mean Faster  
**Video B:** Building an SPSC Ring Buffer and Measuring Every Nanosecond

## Week 18 — Thread pools, work queues, false sharing and concurrency capstone
**Phase:** Concurrency & C++ Memory Model  
**Dates:** 2026-12-07 to 2026-12-13  
**Read:** Anthony Williams thread-pool/concurrent design sections. Fedor concurrency performance sections.  
**Build / break / measure:** Build CppValley runtime: thread pool, bounded queue, futures/tasks, shutdown, per-thread counters. Profile contention and false sharing. Add benchmarks and TSan.  
**Mastery gate:** Concurrency mock >=80%. Explain scaling ceiling, task granularity, false sharing, work stealing concept, shutdown semantics and benchmark evidence.  
**DSA:** Graph mixed review  
**Video A:** How Would You Design a Thread Pool in a Staff Interview?  
**Video B:** I Built and Profiled a C++ Thread Pool From Scratch
