# DreamRun Roadmap — Weeks 1-10

## Week 01 — Type deduction, cv/ref qualifiers, auto, decltype
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-08-10 to 2026-08-16  
**Read:** Scott Meyers Items 1-6. cppreference: type deduction, auto, decltype, references, cv qualifiers. C++ Core Guidelines: type/interface basics.  
**Build / break / measure:** Create 50 compile-time deduction cases using static_assert/std::is_same_v. Predict T before compiling. Compare by-value, T&, const T&, T&&, arrays, functions, pointers. Inspect 10 cases in Compiler Explorer.  
**Mastery gate:** Explain reference collapsing; decltype(x) vs decltype((x)); array/function decay; top-level vs low-level const. Score >=90% on your own 50-case closed-book quiz.  
**DSA:** Arrays: prefix/suffix, frequency, in-place  
**Video A:** C++ Type Deduction: The Staff Interview Most Engineers Fail  
**Video B:** I Tested 50 Type-Deduction Cases So You Don't Have To

## Week 02 — Storage duration, object lifetime, initialization, RAII
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-08-17 to 2026-08-23  
**Read:** cppreference: object lifetime, storage duration, initialization, destruction, placement new. Scott Meyers Items 7-10 and relevant Core Guidelines resource rules.  
**Build / break / measure:** Implement Tracked object logging construction/destruction; placement-new experiment; RAII FileDescriptor/File wrapper. Deliberately create dangling references, use-after-scope and lifetime extension cases; diagnose with ASan/UBSan.  
**Mastery gate:** Given code, identify exact lifetime begin/end and ownership. Explain temporary lifetime extension, static/thread/local storage, initialization order and why RAII works.  
**DSA:** Hash maps/sets + strings  
**Video A:** C++ Object Lifetime: The Rule Behind Thousands of Bugs  
**Video B:** I Created 10 Lifetime Bugs and Let Sanitizers Hunt Them

## Week 03 — Special member functions, Rule of 0/5, smart-pointer ownership
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-08-24 to 2026-08-30  
**Read:** Scott Meyers Items 17-22. cppreference: copy/move constructors, assignments, destructor, unique_ptr/shared_ptr/weak_ptr. Core Guidelines ownership sections.  
**Build / break / measure:** Build move-only FileHandle and educational UniquePtr<T>. Build simplified ref-counted pointer/control block. Create shared_ptr cycle and fix with weak_ptr. Test exception and self-move behavior.  
**Mastery gate:** Write a correct move-only RAII class from memory. Explain when compiler generates/deletes special members, shared_ptr control block, make_shared trade-off and cyclic ownership.  
**DSA:** Two pointers  
**Video A:** Rule of Zero vs Rule of Five: What Senior C++ Interviews Really Test  
**Video B:** I Built unique_ptr and Reference Counting From Scratch

## Week 04 — Value categories, move semantics, forwarding, copy elision
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-08-31 to 2026-09-06  
**Read:** Scott Meyers Items 23-30. cppreference: value categories, std::move, std::forward, copy elision, forwarding references.  
**Build / break / measure:** Instrument copies/moves/allocations across return-by-value, vector insertion, pass-by-value/ref, perfect forwarding. Build invoke_and_log with perfect forwarding. Compile with/without elision where supported.  
**Mastery gate:** Explain lvalue/xvalue/prvalue; why std::move does not move; forward<T>; noexcept and move; mandatory copy elision. Write forwarding wrapper without notes.  
**DSA:** Sliding window  
**Video A:** std::move Does NOT Move Anything  
**Video B:** I Counted Every Copy and Move in a Real C++ Program

## Week 05 — Templates, variadics, constexpr, concepts and constraints
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-09-07 to 2026-09-13  
**Read:** Scott Meyers Items 31-34 for lambdas plus cppreference: templates, parameter packs, constexpr, if constexpr, concepts/requires. Core Guidelines generic programming sections.  
**Build / break / measure:** Build type-safe tagged units or policy-based utility; variadic logger; constrained generic algorithm; replace SFINAE-style overload with concepts. Write compile-fail tests for bad constraints.  
**Mastery gate:** Explain instantiation, dependent names, overload resolution at a practical level, parameter packs, constexpr evaluation, concepts vs enable_if. Design readable template diagnostics.  
**DSA:** Binary search + binary search on answer  
**Video A:** Templates Without Magic: How the Compiler Sees Generic C++  
**Video B:** I Replaced Ugly SFINAE With C++20 Concepts

## Week 06 — STL containers, iterators, complexity, invalidation
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-09-14 to 2026-09-20  
**Read:** cppreference container pages: vector/deque/list/map/unordered_map/set/string; iterator categories; complexity and invalidation tables. Review Meyers relevant API advice.  
**Build / break / measure:** Benchmark vector/deque/list for traversal/insertion workloads. Build LRU cache from list+unordered_map. Create iterator invalidation test suite. Compare reserve/no-reserve.  
**Mastery gate:** Choose a container from workload, not folklore. Explain invalidation, node vs contiguous storage, hash load factor, rehashing and why Big-O alone is insufficient.  
**DSA:** Linked lists  
**Video A:** vector vs list: Big-O Lied to You  
**Video B:** I Benchmarked the STL Containers Under Real Workloads

## Week 07 — Raw storage, allocators, vector internals, exception guarantees
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-09-21 to 2026-09-27  
**Read:** cppreference: allocator model, allocator_traits, placement new, alignment, exception safety. Fedor Pikus: measurement basics. Core Guidelines resource management.  
**Build / break / measure:** Build educational Vector<T>: allocate raw storage, construct/destroy elements, grow capacity, move_if_noexcept, strong exception guarantee. Build simple arena/fixed pool.  
**Mastery gate:** Explain strong/basic/no-throw guarantees, alignment, capacity growth, move_if_noexcept, allocator role. Survive injected constructor exceptions without leaks/corruption.  
**DSA:** Stacks/queues + monotonic stack  
**Video A:** How std::vector Grows: Allocation, Move, Destruction  
**Video B:** I Built a Vector From Raw Memory — Then Broke Exception Safety

## Week 08 — Runtime polymorphism, layout, vtables, RTTI, type erasure intro
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-09-28 to 2026-10-04  
**Read:** cppreference: virtual functions, abstract classes, dynamic_cast, typeid. Iglberger: abstractions/value semantics/type erasure preview. Compiler Explorer for layout calls.  
**Build / break / measure:** Inspect vptr/vtable experimentally; measure virtual vs function pointer vs std::function baseline; build small Shape system with inheritance, variant and type-erasure alternatives.  
**Mastery gate:** Explain object slicing, virtual destructors, devirtualization concept, RTTI costs/use, runtime vs compile-time polymorphism and trade-offs.  
**DSA:** Recursion/backtracking  
**Video A:** Virtual Functions: What Actually Happens at Runtime?  
**Video B:** Inheritance vs Variant vs Type Erasure — Same Problem, Three Designs

## Week 09 — Translation units, preprocessor, ODR, linking, ABI, CMake
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-10-05 to 2026-10-11  
**Read:** CS:APP linking chapter/sections. cppreference translation phases/ODR. Read docs for nm, readelf, objdump, ldd. CMake official tutorial selectively.  
**Build / break / measure:** Create multi-library project with static/shared libs. Deliberately trigger undefined reference, multiple definition, symbol visibility and ABI break examples. Inspect symbols and mangling.  
**Mastery gate:** Diagnose linker errors from command line. Explain ODR, templates in headers, name mangling, static vs shared libs, ABI compatibility, PImpl motivation.  
**DSA:** Intervals + sorting  
**Video A:** From .cpp to Executable: Every Stage Explained  
**Video B:** I Broke the C++ Linker 12 Different Ways

## Week 10 — Undefined behavior, sanitizers, debugging, testing and C++ mastery gate
**Phase:** C++ Language & Toolchain Mastery  
**Dates:** 2026-10-12 to 2026-10-18  
**Read:** cppreference UB overview; Clang/GCC sanitizer docs; GoogleTest docs; C++ Core Guidelines safety/error-handling sections. Revisit weak Scott items.  
**Build / break / measure:** Build a 'bug zoo': UAF, OOB, signed overflow, uninitialized read, data race placeholder, bad downcast. Diagnose with ASan/UBSan/gdb. Add unit/property-style tests to prior labs.  
**Mastery gate:** 90-minute closed-book C++ mock: types, lifetime, move, templates, STL, ABI, debugging. Must score >=80%; any weak domain becomes a repeat week before Phase 2.  
**DSA:** Mixed fundamentals review  
**Video A:** Undefined Behavior: Code That Compiles, Runs, and Betrays You  
**Video B:** My 90-Minute Staff C++ Mastery Test
