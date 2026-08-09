# DreamRun Master Plan

This is the **only canonical overall plan** for DreamRun.

DreamRun is not organized around a fixed number of weeks or uploads. It is organized around **dependency order and mastery gates**. Calendar dates are tracking aids, not reasons to move on from a weak topic.

## Target outcomes

The long-term target profile is a systems-focused engineer who can credibly interview for:

- HFT / low-latency C++ engineering
- Google-style infrastructure / systems roles
- Staff / Principal / C++ Architect roles
- GPU / CUDA systems engineering
- AI infrastructure / inference systems architecture

The goal is not to become a generic ML researcher or a shallow generalist across all of these areas.

## Curriculum order

### 1. Modern C++ mastery

Deep language semantics, object lifetime, value categories, ownership, generic programming, STL, modern language/library features, ABI/toolchain, testing/debugging, and practical implementation.

Primary spine:
- Scott Meyers, *Effective Modern C++* — all 42 items, no compression requirement.
- cppreference for exact semantics.
- C++ Core Guidelines for design/safety guidance.
- Compiler Explorer, GCC/Clang, sanitizers and debugger for proof.

The detailed current syllabus lives in [`curriculum/01-cpp-mastery.md`](curriculum/01-cpp-mastery.md).

### 2. Concurrency and the C++ memory model

Only after the language/ownership foundation is strong:
- thread lifetime and cancellation
- mutexes and locking design
- condition variables, semaphores, barriers and futures
- thread-safe interface design
- C++ abstract-machine memory model
- atomics and memory orderings
- CAS
- lock-free progress guarantees
- ABA and memory reclamation concepts
- practical queues, ring buffers and thread pools

Primary spine: Anthony Williams + cppreference + experiments + ThreadSanitizer.

### 3. CPU, memory and performance engineering

- rigorous benchmarking
- compiler optimization
- assembly literacy
- branch prediction and pipelines
- cache hierarchy and locality
- TLB/pages
- allocation and arenas
- false sharing
- affinity/NUMA concepts
- SIMD/vectorization
- perf/profilers
- throughput vs latency vs tail latency

Primary spine: Fedor Pikus + CS:APP + architecture manuals as references + perf/Compiler Explorer.

### 4. Linux systems and networking

- processes, syscalls, signals, virtual memory and mmap
- files and file descriptors
- sockets
- TCP/UDP
- binary protocols and serialization
- multicast
- blocking/nonblocking I/O
- select/poll/epoll
- backpressure
- profiling real servers

### 5. Low-latency / HFT engineering

Synthesize C++, concurrency, CPU, memory, Linux and networking into engineering problems such as:
- latency measurement and jitter
- zero/low-allocation hot paths
- feed handlers
- sequence/gap handling
- order-book data structures
- matching-engine correctness
- gateways and validation
- ring buffers and memory pools
- tail-latency analysis
- end-to-end profiling

This is software-engineering preparation, not a promise of trading/quant expertise.

### 6. C++ architecture and Staff-level design

- coupling, cohesion and dependency management
- abstraction boundaries
- runtime vs compile-time polymorphism
- composition/value semantics/type erasure
- Strategy/Command/Observer/Adapter/Bridge/CRTP/PImpl where justified
- API/ABI stability
- error models
- testing seams and observability
- ADRs and architectural trade-offs
- sanitized Staff-level technical leadership stories

Primary spine: Klaus Iglberger + real refactoring of DreamRun projects.

### 7. Distributed systems

- persistence/logs
- replication
- partitioning/sharding
- consistency models
- retries/idempotency
- transactions at an architectural level
- queues/logs/streams
- backpressure and overload
- failure detection
- consensus concepts
- system-design interviewing

Primary spine: DDIA for depth; Alex Xu for interview framing.

### 8. CUDA / GPU systems

- GPU execution model
- warps/blocks/grids
- memory hierarchy
- coalescing
- synchronization/divergence
- reductions
- tiling/matmul
- occupancy
- streams/asynchronous execution
- transfer/computation overlap
- Nsight-guided optimization

Primary spine: NVIDIA CUDA Programming Guide + Best Practices + Nsight Compute.

### 9. AI fundamentals and inference systems

Learn AI through the systems lens:
- linear algebra refresh
- MLP/forward pass
- backpropagation
- transformer tensor flow
- attention
- training vs inference
- prefill/decode
- KV cache
- batching
- quantization concepts
- model-serving architecture
- GPU memory/capacity planning
- overload/observability

The target is **AI infrastructure / inference systems**, not generic data science.

### 10. Interview conversion

Interview preparation becomes dominant only after the technical base exists:
- timed DSA
- C++ deep-dive mocks
- concurrency/performance mocks
- HFT systems mocks
- C++ architecture reviews
- distributed/system-design mocks
- CUDA/AI-infrastructure design mocks
- Staff/Principal behavioral and influence stories
- role-specific resume and portfolio positioning

## Mastery gate

A concept is not complete because the chapter was read or a video was recorded. Before moving on, be able to:

- explain it without notes
- implement the core idea where appropriate
- identify invariants
- create and diagnose failure cases
- discuss performance implications
- choose among alternatives
- answer escalating interview questions
- state what you still do not know

If a gate fails, repeat the weak layer. Do not advance because a date arrived.

## CppValley rule

There is **no target number of videos per week**.

After mastering a concept, extract as many videos as are technically justified. For example, one Scott Meyers item may naturally become several videos: mental model, compiler experiment, implementation, edge cases, benchmark, and interview drill.

Do not combine unrelated ideas merely to keep a publishing schedule.

## Parallel DSA retention track

Use one structured learning source and one curated interview set. The key mechanism is spaced retrieval, not course accumulation.

For each important problem, record:
- pattern recognition signals
- brute-force approach
- optimized invariant
- complexity
- mistakes made
- edge cases
- next review date

Prefer revisiting patterns on D+2, D+7, D+21, D+60 and D+120.

## Projects

Projects appear only when the prerequisite concepts are mastered. Expected long-running projects include:

- CppValley Runtime — concurrency/performance primitives
- CppValley KV — Linux/networking/distributed-system experiments
- CppValley Exchange — low-latency/HFT engineering
- CppValley Inference — C++/CUDA/AI-inference experiments

Do not create empty project folders just for optics. Add real code when the project begins.

## Revision policy

When DreamRun evolves, **edit the canonical plan**. Do not keep competing `v1`, `v2`, old-weekly-plan, or archived roadmap files in the main repository.