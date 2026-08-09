# Curriculum 01 — Modern C++ Mastery

This is the **current active DreamRun curriculum**.

There is no requirement to finish it in a fixed number of weeks and no limit on how many CppValley videos it may produce. Scott Meyers alone may generate dozens or 100+ videos if the experiments and explanations justify them.

## Primary sources and tools

1. **Scott Meyers — Effective Modern C++**: all 42 items are mandatory coverage.
2. **cppreference**: exact language/library semantics and modern C++17/20/23 extensions — https://en.cppreference.com/w/
3. **C++ Core Guidelines**: ownership, interfaces, resource management, generic programming, concurrency and safety — https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines
4. **Compiler Explorer**: generated code/diagnostics — https://godbolt.org/
5. **GCC + Clang** with aggressive warnings.
6. **ASan / UBSan / TSan** where relevant.
7. **gdb/lldb**, `nm`, `readelf`, `objdump`, `ldd` for toolchain/runtime investigation.

## How to study every item

For every item/subtopic create a mastery unit using [`../templates/mastery-unit.md`](../templates/mastery-unit.md).

Minimum evidence before marking a unit complete:

- closed-book explanation
- at least one minimal correct example
- edge-case matrix
- at least one intentionally broken example when applicable
- compiler/runtime/tool evidence when applicable
- interview questions from basic → senior → Staff depth
- explicit trade-offs and non-applicability
- video ideas extracted only after mastery

---

# Part A — Scott Meyers, all 42 items

The themes below intentionally map every item. Do not skip an item because it looks familiar.

## Block 1 — Type deduction: Items 1–4

### Item 1 — Template type deduction
Master:
- by-value parameters
- lvalue-reference parameters
- const-reference parameters
- forwarding-reference deduction
- arrays and functions
- top-level vs low-level cv qualifiers
- reference stripping and decay

Required experiments:
- build 50–100 `static_assert(std::is_same_v<...>)` cases
- predict `T` and parameter type before compiling
- compare array/function behavior by value vs reference
- create a closed-book deduction quiz

Possible video families:
- template deduction mental model
- array/function decay
- cv/ref interview traps
- compiler-driven deduction lab

### Item 2 — `auto` deduction
Master:
- how `auto` follows template-deduction-like rules
- reference/cv behavior
- `auto&`, `const auto&`, `auto&&`
- initializer-list special behavior
- dangerous readability/type-surprise cases

Required experiments:
- rewrite Item 1 matrix using `auto`
- compare `auto`, `auto&`, `auto&&`, `const auto&`
- investigate brace initialization differences

### Item 3 — `decltype`
Master:
- `decltype(name)` vs `decltype((expression))`
- lvalue/xvalue/prvalue effects
- references returned by `decltype`
- interaction with forwarding and generic APIs

Required experiments:
- at least 30 expression cases
- `decltype(x)` vs `decltype((x))` matrix
- functions returning `decltype(auto)` later in the extension block

### Item 4 — Viewing deduced types
Master:
- compiler errors as a type-inspection technique
- `type_traits`/`static_assert`
- IDE/debugger limitations
- type-display helpers and why printed type names can mislead

Required experiments:
- three independent ways to inspect a type
- cases where runtime type-name output loses qualifiers/references

**Block gate:** solve a 100-case mixed deduction exam with >=90% accuracy closed-book.

---

## Block 2 — `auto`: Items 5–6

### Item 5 — Prefer `auto` where it improves correctness/maintainability
Master:
- iterator types
- closure types
- avoiding accidental narrowing/copy from explicit types
- when explicit types communicate intent better

Required experiments:
- map/unordered-map iteration with subtly wrong explicit element types
- lambda closure storage
- refactoring type changes with/without `auto`

### Item 6 — Avoid unintended proxy/invisible expression types
Master:
- proxy references and expression templates conceptually
- `vector<bool>`-style proxy behavior
- delayed conversions
- why `auto` can preserve a proxy instead of materializing a value

Required experiments:
- proxy-returning educational type
- lifetime/conversion bug caused by `auto`
- explicit materialization fix

**Block gate:** given unfamiliar API expressions, reason about whether `auto` preserves the intended value/reference/proxy semantics.

---

## Block 3 — Moving to modern C++: Items 7–17

### Item 7 — Brace initialization
Master:
- uniform initialization forms
- narrowing prevention
- `initializer_list` preference in overload resolution
- constructor ambiguity
- `vector` size/value vs initializer-list traps

Experiments:
- exhaustive constructor-overload matrix with `()`, `{}`, `={}`
- narrowing compilation cases

### Item 8 — `nullptr`
Master:
- why `0`/`NULL` can behave as integers
- overload resolution
- templates and pointer APIs

Experiments:
- overload set with integral and pointer candidates
- template forwarding cases

### Item 9 — Alias declarations vs `typedef`
Master:
- readability
- alias templates
- dependent types and template aliases

Experiments:
- traits/allocator/container aliases
- template alias replacing nested typedef machinery

### Item 10 — Scoped enums
Master:
- scope pollution
- implicit integer conversions
- underlying type
- forward declaration

Experiments:
- API with unscoped enum bugs vs `enum class`
- serialization/underlying-value access

### Item 11 — Deleted functions
Master:
- disabling copy/operations
- deleting overloads
- preventing unsafe conversions
- accessibility vs deletion

Experiments:
- deleted overload set preventing `char`/`bool`/pointer misuse
- compare private declaration vs `= delete`

### Item 12 — `override`
Master:
- override mismatches from cv/ref qualifiers
- signature changes
- virtual dispatch correctness

Experiments:
- intentionally broken overrides
- ref-qualified member functions

### Item 13 — `const_iterator`
Master:
- iterator mutability
- APIs accepting iterator/const_iterator
- generic algorithms and const-correctness

Experiments:
- insertion/erase/search workflows using const iterators

### Item 14 — `noexcept`
Master:
- semantic contract
- termination behavior
- conditional `noexcept`
- standard-container optimization implications

Experiments:
- vector relocation with throwing vs `noexcept` move constructor
- `std::is_nothrow_move_constructible_v`

### Item 15 — `constexpr`
Master:
- compile-time vs runtime usability
- constexpr functions/objects
- restrictions by language version
- constant evaluation as design tool

Experiments:
- constexpr math/type utility
- compile-time validation
- compare C++14/17/20 capabilities where practical

### Item 16 — Thread-safe `const` member functions
Master:
- logical vs physical constness
- `mutable`
- synchronization in const functions
- caches/lazy initialization

Experiments:
- const cache with race
- mutex/atomic fixes

### Item 17 — Special member function generation
Master:
- Rule of Zero / Five
- compiler generation/deletion
- impact of user-declared destructor/copy/move
- member/base constraints

Experiments:
- matrix of classes with different user-declared special members
- `static_assert` traits for copy/move constructibility/assignability

**Block gate:** design a resource-owning type and justify initialization, deletion, `noexcept`, constness and special-member behavior without notes.

---

## Block 4 — Smart pointers and ownership: Items 18–22

### Item 18 — `unique_ptr`
Master:
- exclusive ownership
- custom deleters
- object size implications
- arrays
- incomplete types/PImpl considerations
- move-only APIs

Build:
- educational `UniquePtr<T>`
- custom deleter examples
- PImpl example

### Item 19 — `shared_ptr`
Master:
- control block
- strong count
- custom deleter location
- aliasing constructor concept
- atomic reference-count implications
- ownership vs raw observer pointers

Build:
- simplified educational reference-counted pointer
- inspect sizes/allocations

### Item 20 — `weak_ptr`
Master:
- non-owning observation
- `lock()`
- expiration
- cycles
- caches/observer scenarios

Experiments:
- shared cycle leak
- break it with weak ownership

### Item 21 — `make_unique` / `make_shared`
Master:
- exception-safety motivation
- allocation count
- control-block/object co-allocation
- lifetime/memory-retention trade-off with weak references
- custom-deleter limitations

Experiments:
- instrument allocations
- weak pointer retaining combined allocation scenario conceptually/experimentally

### Item 22 — PImpl with smart pointers
Master:
- incomplete types
- destructor definition placement
- ABI/compile-time dependency motivation
- ownership semantics

Build:
- small shared library with PImpl and implementation changes

**Block gate:** given an ownership graph, mark owners/observers and choose `unique_ptr`, `shared_ptr`, `weak_ptr`, references or raw observer pointers with justification.

Potential CppValley depth from this block alone may be large: internals, implementations, cycles, allocation behavior, PImpl, API design and interview drills should not be compressed artificially.

---

## Block 5 — Rvalue references, move semantics and perfect forwarding: Items 23–30

### Item 23 — `std::move` / `std::forward`
Master:
- casts, not operations
- move from const
- overload selection
- forwarding preservation

### Item 24 — Forwarding references vs rvalue references
Master:
- exact syntactic/context conditions
- deduction
- `auto&&`
- reference collapsing

### Item 25 — Applying move/forward correctly
Master:
- last-use discipline
- forwarding once
- member forwarding
- return-value anti-patterns

### Item 26 — Universal/forwarding-reference overload hazards
Master:
- greedy overloads
- unexpected matches
- copy/move constructor interference

### Item 27 — Alternatives to forwarding-reference overloads
Master:
- distinct function names
- const-reference overloads
- pass-by-value
- tag dispatch / constraints

### Item 28 — Reference collapsing
Master:
- all collapse combinations
- why forwarding works
- typedef/alias/decltype interactions

### Item 29 — When move is not actually faster
Master:
- missing move operations
- const objects
- small/trivial types
- SSO and implementation realities
- noexcept/container behavior

### Item 30 — Perfect-forwarding failure cases
Master:
- braced initializers
- null pointer constants
- static const integral members/ODR history
- overloaded function names/templates
- bit-fields

Required builds/experiments for Block 5:
- `Tracked` type counting copy/move/destruction
- perfect-forwarding wrapper
- forwarding-constructor hazard example
- copy-elision/RVO experiments
- vector relocation + `noexcept`
- intentionally failing forwarding cases
- Compiler Explorer inspection

**Block gate:** explain value categories/reference collapsing and write a correct forwarding wrapper from memory; diagnose why a given 'move' copied.

---

## Block 6 — Lambdas: Items 31–34

### Item 31 — Avoid default capture modes
Master:
- implicit capture maintenance hazards
- `this` capture semantics
- lifetime issues

### Item 32 — Init capture / moving objects into closures
Master:
- generalized lambda capture
- move-only state
- ownership inside closures

### Item 33 — `decltype`/forwarding in generic lambdas
Master:
- `auto&&` parameters
- preserving value category
- forwarding from lambda parameters

### Item 34 — Prefer lambdas over `std::bind`
Master:
- readability
- overload handling
- forwarding
- evaluation/capture semantics

Required experiments:
- dangling `this` capture
- move-only capture
- generic forwarding lambda
- lambda vs `std::bind` behavior and generated code

---

## Block 7 — Concurrency API preview from Scott: Items 35–40

These items are mastered here at the API/modern-C++ level, then revisited much more deeply in the Anthony Williams concurrency curriculum.

### Item 35 — Task-based vs raw-thread programming
Explore futures/tasks, result/exception propagation and composability.

### Item 36 — `std::async` launch policies
Explore deferred vs asynchronous execution and policy uncertainty.

### Item 37 — Thread joinability
Master lifecycle rules and termination hazards.

### Item 38 — Thread-handle/destructor strategies
Explore joining, detaching and ownership problems; compare later with `std::jthread`.

### Item 39 — One-shot event notification patterns
Explore condition-variable/promise-future approaches and their trade-offs.

### Item 40 — Atomics vs `volatile`
Master that C++ `volatile` is not a synchronization primitive; build data-race examples and atomic alternatives.

**Block gate:** explain the limitations of the C++11/14 concurrency API and identify what requires the later full concurrency curriculum.

---

## Block 8 — Tweaks: Items 41–42

### Item 41 — Pass-by-value when copying movable parameters is appropriate
Master:
- overload alternatives
- copy vs move counts
- slicing/ownership caveats
- strong-exception-safety/design considerations

Experiments:
- setter APIs with const-ref/rvalue-ref overloads vs pass-by-value
- count operations for lvalue/rvalue callers

### Item 42 — `emplace` vs insert/push
Master:
- when emplacement avoids temporaries
- when it does not
- explicit-constructor surprises
- resource-management safety differences

Experiments:
- `push_back` vs `emplace_back` construction counts
- explicit-conversion examples
- smart-pointer/resource insertion safety case

**Scott completion gate:** closed-book interview covering all eight blocks plus practical code review. Passing Scott is not the end of C++ mastery; it unlocks the modern extensions below.

---

# Part B — C++17 mastery extensions

Scott predates these. Cover them deliberately rather than assuming familiarity.

## Language
- structured bindings
- `if constexpr`
- fold expressions
- class template argument deduction (CTAD)
- inline variables
- guaranteed copy elision refinements
- nested namespace syntax and selected usability improvements

## Library
- `std::optional`
- `std::variant`
- `std::any`
- `std::string_view`
- `std::filesystem`
- `std::byte`
- parallel algorithm model/constraints
- `std::invoke` / `std::apply`

Required projects/experiments:
- variant-based state machine vs inheritance
- optional/error modeling trade-offs
- string_view lifetime bug zoo
- filesystem tool
- fold-expression utilities
- CTAD deduction-guide examples

**Gate:** confidently choose modern vocabulary types and identify their lifetime/ownership traps.

---

# Part C — C++20 mastery extensions

## Concepts and constraints
- requires clauses/expressions
- named concepts
- subsumption/overload selection at a practical level
- replacing SFINAE-heavy APIs

## Ranges
- views vs owning ranges
- lazy pipelines
- dangling/lifetime concerns
- projections
- algorithms + ranges design

## Coroutines
- coroutine mental model
- suspension/resumption
- promise type concept
- awaiter/awaitable concept
- lifetime and allocation concerns
- build an educational coroutine/task type only after the model is clear

## Concurrency/library
- `std::jthread`
- `stop_token`
- semaphores
- latches
- barriers
- `std::atomic_ref`

## Other important facilities
- `std::span`
- three-way comparison
- expanded constexpr/consteval/constinit
- modules: understand the model/build implications even if toolchain practice is limited
- `std::source_location`
- formatting library basics

Required experiments:
- replace an enable_if/SFINAE API with concepts
- range pipeline with lifetime tests
- minimal coroutine trace showing every suspend/resume point
- cancellation with `jthread`
- span API replacing pointer+size

---

# Part D — C++23 mastery extensions

Prioritize features useful for systems/API work rather than memorizing the entire standard.

Core candidates:
- `std::expected`
- `std::move_only_function`
- `std::forward_like`
- `std::mdspan`
- `std::print`
- `std::stacktrace`
- selected ranges improvements
- selected language improvements relevant to cleaner generic/API code

For each feature answer:
- what older pattern does it replace?
- what ownership/lifetime semantics does it introduce?
- what are its ABI/performance implications?
- is compiler/library support sufficient for the intended environment?

---

# Part E — STL and standard-library internals track

Run alongside Parts A–D once prerequisite language concepts are ready.

Master practically:
- `vector`, `deque`, `list`
- `map`/`set`
- `unordered_map`/`unordered_set`
- `string`
- iterators and iterator invalidation
- allocator model
- algorithms
- comparator/hash requirements
- exception guarantees
- container complexity vs memory locality

Build educational versions where useful:
- `Vector<T>` using raw storage + placement construction
- arena/fixed-size allocator
- LRU cache
- simplified callable/type-erasure wrapper later

Measure:
- reserve/no reserve
- contiguous vs node-based traversal
- hash load/rehash behavior
- insertion/search workloads
- allocation counts

---

# Part F — C++ object model, ABI and toolchain track

Master:
- storage duration/lifetime
- alignment/padding/layout
- virtual dispatch/vtables as implementation concepts
- object slicing
- RTTI/dynamic_cast
- compilation phases
- translation units
- ODR
- name mangling
- static/shared libraries
- symbol visibility
- templates across translation units
- ABI stability
- PImpl
- exceptions/unwinding conceptually

Use:
- Compiler Explorer
- `nm`
- `readelf`
- `objdump`
- `ldd`
- debugger

Required failure labs:
- undefined reference
- multiple definition
- symbol visibility problem
- ABI-breaking class-layout change
- missing virtual destructor
- RTTI/cast failures

---

# Part G — Correctness, testing and debugging track

Build a C++ bug zoo covering:
- use-after-free
- use-after-scope
- out-of-bounds
- double free
- signed overflow / UB examples
- invalid iterator use
- dangling string_view/span/reference
- bad downcast
- data race later

Use:
- AddressSanitizer
- UndefinedBehaviorSanitizer
- ThreadSanitizer later
- gdb/lldb
- unit tests
- fuzz/property-style thinking where useful

The goal is not merely to know safe syntax; it is to diagnose real failures.

---

# CppValley extraction policy

Do **not** assign a fixed video count to any block.

After a mastery unit passes, extract videos based on technical value. A single item can produce multiple distinct formats:

1. mental-model explanation
2. interview-trap episode
3. compiler/assembly investigation
4. build-it-from-scratch implementation
5. bug/debugging episode
6. benchmark/performance episode
7. API/design trade-off episode
8. closed-book mock interview

A topic with enough depth may legitimately produce 5–10+ videos.

Never combine topics solely to reduce the number of uploads.

# C++ completion criteria

Do not declare the C++ phase complete until you can:

- explain every Scott Meyers item without rereading the book
- reason accurately about lifetime, ownership, value categories and deduction
- implement nontrivial generic/resource-owning types
- understand modern C++17/20/23 facilities relevant to systems work
- select STL containers based on semantics and workload
- diagnose sanitizer/debugger/toolchain failures
- read useful compiler output/assembly at a practical level
- discuss ABI/API trade-offs
- pass repeated senior/Staff C++ mock interviews without recurring conceptual gaps

Only then does DreamRun make concurrency the next primary curriculum.