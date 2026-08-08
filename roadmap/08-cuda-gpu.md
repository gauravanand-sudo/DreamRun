# DreamRun Roadmap — Weeks 49-54

## Week 49 — GPU architecture and CUDA programming model
**Phase:** CUDA / GPU Systems  
**Dates:** 2027-07-12 to 2027-07-18  
**Read:** NVIDIA CUDA Programming Guide: intro, programming model, kernels, grid/block/thread, heterogeneous model. CUDA Best Practices intro.  
**Build / break / measure:** Set up personal NVIDIA-capable environment if available. Write vector add, SAXPY and simple kernels. Vary block size, validate results, compare transfer vs compute.  
**Mastery gate:** Explain CPU vs GPU execution model, warp/block/grid, kernel launch, host/device memory and when GPU overhead dominates.  
**DSA:** Unseen medium + one hard stretch  
**Video A:** CPU vs GPU: What Actually Changes Architecturally?  
**Video B:** My First CUDA Kernel — Every Thread Accounted For

## Week 50 — GPU memory hierarchy, coalescing and transfers
**Phase:** CUDA / GPU Systems  
**Dates:** 2027-07-19 to 2027-07-25  
**Read:** CUDA Programming Guide memory hierarchy. Best Practices memory optimization sections.  
**Build / break / measure:** Benchmark coalesced vs strided global memory; pageable vs pinned transfer if supported; shared-memory staging simple lab.  
**Mastery gate:** Explain global/shared/register/local/constant memory conceptually, coalescing, transfer overhead and bandwidth-bound behavior.  
**DSA:** Unseen medium + one hard stretch  
**Video A:** GPU Memory Is the Real Performance Problem  
**Video B:** I Broke Memory Coalescing and Watched CUDA Slow Down

## Week 51 — Synchronization, reductions, shared memory and divergence
**Phase:** CUDA / GPU Systems  
**Dates:** 2027-07-26 to 2027-08-01  
**Read:** CUDA Guide synchronization/shared memory/warp behavior. Best Practices relevant sections.  
**Build / break / measure:** Implement reduction: naive -> shared memory -> improved stages. Create divergent vs uniform branch experiment. Profile.  
**Mastery gate:** Explain __syncthreads scope, race hazards, divergence and why reduction design changes memory traffic.  
**DSA:** Trees/graphs timed  
**Video A:** CUDA Synchronization: One Missing Barrier, Wrong Answer  
**Video B:** I Optimized a GPU Reduction Step by Step

## Week 52 — Matrix multiplication, tiling and occupancy
**Phase:** CUDA / GPU Systems  
**Dates:** 2027-08-02 to 2027-08-08  
**Read:** CUDA Guide tiled examples; Best Practices shared memory/occupancy sections; Nsight Compute basics.  
**Build / break / measure:** CPU matmul baseline, naive CUDA, tiled shared-memory CUDA. Measure kernel time and transfers separately. Use Nsight metrics.  
**Mastery gate:** Explain arithmetic intensity concept, tiling, occupancy vs performance, shared-memory limits and bottleneck evidence.  
**DSA:** DP timed  
**Video A:** Naive CUDA Matrix Multiply Is Surprisingly Bad  
**Video B:** Tiling Made My Kernel Faster — Nsight Shows Why

## Week 53 — Streams, asynchronous execution, pinned memory and pipeline overlap
**Phase:** CUDA / GPU Systems  
**Dates:** 2027-08-09 to 2027-08-15  
**Read:** CUDA Guide streams/async execution. Best Practices transfer/overlap sections.  
**Build / break / measure:** Build H2D -> kernel -> D2H pipeline; add streams and chunking; measure overlap. Explore multiple streams and pinned memory if supported.  
**Mastery gate:** Explain default stream concept, synchronization points, async copies, pinned-memory trade-offs and overlap constraints.  
**DSA:** Binary search/greedy timed  
**Video A:** CUDA Streams: Concurrency or Just More Complexity?  
**Video B:** I Overlapped Copy and Compute — Timeline Proof

## Week 54 — CUDA profiling/optimization capstone
**Phase:** CUDA / GPU Systems  
**Dates:** 2027-08-16 to 2027-08-22  
**Read:** Nsight Compute docs; Best Practices complete review of applicable sections.  
**Build / break / measure:** Choose one kernel from prior weeks. Baseline -> profile -> hypothesis -> change -> profile again. Produce optimization report with metrics and limits.  
**Mastery gate:** CUDA mock >=80%. Given profiler symptoms, identify likely compute/memory/occupancy/transfer bottleneck and propose evidence-based next step.  
**DSA:** Coding mock + review  
**Video A:** Stop Guessing GPU Performance — Read the Profiler  
**Video B:** Full CUDA Optimization: Baseline to Final Kernel
