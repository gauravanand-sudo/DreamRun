# Curriculum 01 — Modern C++ Mastery

This is the **canonical C++ curriculum for DreamRun**.

It is intentionally larger than Scott Meyers. The objective is not to finish a book, memorize trivia, or hit an upload count. The objective is that, for C++-heavy interviews and real systems work, **C++ itself is not the reason you fail**.

There is **no fixed week count and no fixed video count**. One topic may produce one video; another may produce ten. Move on only after the mastery gate is passed.

> Important: Curriculum 01 is the C++ language/library/tooling layer. It does **not** by itself guarantee an offer at Google/FAANG, Adobe, NVIDIA, HFT firms, etc. DSA, concurrency, operating systems, networking, performance, system design, architecture, behavioral/Staff stories, CUDA and AI-infrastructure are separate DreamRun curricula. The exit bar here is: *C++ deep-dive questions should become a strength rather than a risk.*

---

# 0. Source stack — use multiple layers, not one book

## Mandatory spine

1. **Scott Meyers — Effective Modern C++**
   - All **42 items** are mandatory.
   - Do not compress an item merely because it looks familiar.
   - Scott is primarily C++11/C++14; it is not the end of modern C++.

2. **cppreference**
   - Use as the everyday exact-semantics reference for the language and standard library.
   - For every topic, open the relevant language page and the relevant library page.

3. **C++ Core Guidelines**
   - Interfaces, ownership, resource management, expressions, classes, templates, concurrency, error handling and performance guidance.
   - Treat guidelines as engineering guidance, not the language specification.

4. **Compiler Explorer**
   - Compare GCC and Clang.
   - Inspect diagnostics, optimization, inlining, devirtualization, copies/moves and generated assembly when relevant.

5. **GCC + Clang toolchains**
   - Build with aggressive warnings.
   - Typical baseline: `-Wall -Wextra -Wpedantic -Wconversion -Wshadow` plus topic-specific warnings.

6. **Sanitizers**
   - AddressSanitizer (ASan)
   - UndefinedBehaviorSanitizer (UBSan)
   - ThreadSanitizer (TSan — concurrency curriculum in depth)
   - LeakSanitizer where available

7. **Debugger / binary tools**
   - gdb or lldb
   - `nm`
   - `readelf`
   - `objdump`
   - `ldd`
   - compiler optimization reports

## Mandatory depth books by topic

8. **Nicolai Josuttis — C++ Move Semantics: The Complete Guide**
   - Mandatory for the move/forwarding/value-category block.
   - Use it to go beyond Scott on self-move, ref-qualified members, getters, polymorphic hierarchies, perfect returning, move iterators, container move behavior and move-only library types.

9. **David Vandevoorde, Nicolai Josuttis, Douglas Gregor — C++ Templates: The Complete Guide, 2nd Edition**
   - Mandatory template-depth source.
   - All foundational template chapters are required.
   - Advanced chapters are mapped below: dependent names, two-phase lookup, overload resolution, SFINAE, traits, variadics, CRTP, metaprogramming, explicit instantiation and generic-library design.

10. **Nicolai Josuttis — C++17: The Complete Guide**
    - Use to cover C++17 language and library additions systematically.

11. **Nicolai Josuttis — C++20: The Complete Guide**
    - Use for concepts, ranges, coroutines, modules and C++20 library evolution.

12. **Nicolai Josuttis — C++23: The Complete Guide**
    - Use for C++23 additions and their practical traps.

## Strong supporting references

13. **The C++ Standard Library — A Tutorial and Reference, 2nd Edition (Josuttis)**
    - Useful for deep standard-library fundamentals.
    - Cross-check all version-sensitive behavior against current cppreference because the book predates C++17/20/23.

14. **Exceptional C++ / More Exceptional C++ (Herb Sutter) — selected problems**
    - Optional depth source for exception safety, overloads, templates, lifetime and interface design.

15. **Compiler / ABI documentation**
    - Itanium C++ ABI where relevant on Linux toolchains.
    - GCC/Clang docs for implementation-specific behavior.

---

# 1. Mastery protocol for every leaf topic

Create a mastery unit using `templates/mastery-unit.md`.

A leaf topic is not complete until you can check all of these:

- [ ] Explain the concept closed-book in 30 seconds.
- [ ] Explain it again at senior/Staff depth for 5–10 minutes.
- [ ] State the formal rule accurately enough to predict code behavior.
- [ ] Write a minimal correct example from memory.
- [ ] Produce an edge-case matrix.
- [ ] Produce at least one intentionally broken example when applicable.
- [ ] Diagnose the broken example with compiler/debugger/sanitizer evidence when applicable.
- [ ] State ownership and lifetime implications.
- [ ] State exception-safety implications.
- [ ] State compile-time/runtime/performance implications.
- [ ] Compare at least two alternatives.
- [ ] State when **not** to use the feature/idiom.
- [ ] Answer basic → intermediate → senior → Staff follow-ups.
- [ ] Pass a delayed review after at least one week without rereading notes first.
- [ ] Only then extract CppValley videos.

For language rules, do not accept “I know how I normally use it.” You must be able to predict unfamiliar code.

---

# 2. Foundation that Scott Meyers assumes — mandatory before/during Scott

Scott does not reteach the entire C++ language. These foundations are therefore explicit DreamRun requirements.

## 2.1 Translation model and program structure

- [ ] Source file vs translation unit.
- [ ] Preprocessing phases at a practical level.
- [ ] Headers and textual inclusion.
- [ ] Header guards vs `#pragma once` trade-off/portability awareness.
- [ ] Declarations vs definitions.
- [ ] One Definition Rule (ODR).
- [ ] ODR-use.
- [ ] Internal linkage, external linkage, no linkage, module linkage awareness.
- [ ] `static` at namespace scope.
- [ ] `extern`.
- [ ] `inline` functions and inline variables — ODR meaning, not “compiler will inline”.
- [ ] Anonymous namespaces.
- [ ] Namespaces and namespace aliases.
- [ ] Qualified vs unqualified lookup.
- [ ] Argument-dependent lookup (ADL).
- [ ] Hidden-friend idiom.
- [ ] Name hiding.
- [ ] Using-declarations vs using-directives.
- [ ] Forward declarations and incomplete types.
- [ ] Templates across translation units.
- [ ] Explicit instantiation declaration/definition.
- [ ] Basic module model awareness (deep C++20 section later).

### Labs

- Build a three-translation-unit program.
- Intentionally create an ODR violation.
- Create duplicate symbols and undefined references.
- Inspect symbols with `nm`/`readelf`.
- Demonstrate a hidden-friend operator found through ADL.

---

## 2.2 Fundamental types, literals and representation

- [ ] `bool`, character types, signed/unsigned integer types, floating types.
- [ ] `std::size_t`, `std::ptrdiff_t`, fixed-width integer types and when they are/are not guaranteed.
- [ ] Integer ranges and implementation-defined widths.
- [ ] Signed vs unsigned arithmetic.
- [ ] Integer promotions.
- [ ] Usual arithmetic conversions.
- [ ] Signed/unsigned comparison traps.
- [ ] Narrowing conversions.
- [ ] Floating-point representation awareness, NaN/Inf basics.
- [ ] Character encodings at a practical level: `char`, `wchar_t`, `char8_t`, `char16_t`, `char32_t`.
- [ ] Integer/floating/string/character literals.
- [ ] Suffixes.
- [ ] Raw string literals.
- [ ] User-defined literal mechanism awareness.
- [ ] `sizeof`, `alignof`.
- [ ] Alignment and padding.
- [ ] Object representation vs value representation.
- [ ] Endianness concept.
- [ ] Trivially copyable types.
- [ ] Standard-layout types.
- [ ] POD as historical terminology; know why newer trait vocabulary matters.

### Labs

- Print sizes/alignments of multiple aggregates.
- Reorder members and explain padding changes.
- Compare signed/unsigned expressions and warnings.
- Use `std::bit_cast` later to inspect object representation safely for suitable types.

---

## 2.3 Initialization — exhaustive practical model

- [ ] Default-initialization.
- [ ] Value-initialization.
- [ ] Zero-initialization.
- [ ] Direct-initialization.
- [ ] Copy-initialization.
- [ ] Direct-list-initialization.
- [ ] Copy-list-initialization.
- [ ] Aggregate initialization.
- [ ] Reference initialization.
- [ ] Constant initialization.
- [ ] Static initialization vs dynamic initialization awareness.
- [ ] Initialization order of members.
- [ ] Base-before-member construction order.
- [ ] Member declaration order vs initializer-list textual order.
- [ ] Most-vexing parse.
- [ ] `initializer_list` overload preference.
- [ ] Narrowing with braces.
- [ ] Aggregate evolution across C++ versions.
- [ ] Designated initializers (C++20 constraints later).
- [ ] Static initialization order problem.
- [ ] Function-local statics and thread-safe initialization since C++11.

### Lab

Create one `InitTracer` type and test every initialization form; record which constructor/operation is selected.

---

## 2.4 Pointers, references and indirection

- [ ] Object pointers.
- [ ] Function pointers.
- [ ] Pointer-to-member data.
- [ ] Pointer-to-member functions.
- [ ] Null pointer value.
- [ ] Pointer arithmetic rules.
- [ ] One-past-the-end rule.
- [ ] Array-to-pointer decay.
- [ ] Function-to-pointer decay.
- [ ] Lvalue references.
- [ ] Rvalue references.
- [ ] Reference binding rules.
- [ ] References are not reseatable.
- [ ] Reference lifetime vs referred-object lifetime.
- [ ] `const` pointer vs pointer-to-const.
- [ ] Top-level vs low-level cv qualification.
- [ ] `volatile` meaning and its limitations.
- [ ] `std::addressof` awareness.
- [ ] `std::reference_wrapper`.
- [ ] `std::span` later as non-owning contiguous view.

### Gate

Given 30 declaration puzzles, read them correctly and identify mutability, ownership and lifetime.

---

## 2.5 Expressions, sequencing and value categories

- [ ] lvalue.
- [ ] xvalue.
- [ ] prvalue.
- [ ] glvalue.
- [ ] temporary materialization awareness.
- [ ] discarded-value expressions.
- [ ] implicit conversions.
- [ ] lvalue-to-rvalue conversion.
- [ ] qualification conversion.
- [ ] integral/floating conversions.
- [ ] standard conversion sequences at a practical level.
- [ ] user-defined conversions.
- [ ] `explicit` constructors.
- [ ] conversion operators.
- [ ] contextual conversion to `bool`.
- [ ] sequencing vs order of evaluation.
- [ ] unsequenced modification hazards.
- [ ] comma operator vs comma separator.
- [ ] short-circuit evaluation.
- [ ] conditional operator value-category behavior awareness.

---

## 2.6 Functions and overload resolution

- [ ] Declarations and definitions.
- [ ] Parameter passing by value/reference/pointer.
- [ ] Default arguments.
- [ ] Function overloading.
- [ ] Standard conversion ranking at a practical level.
- [ ] User-defined conversions in overload resolution.
- [ ] Deleted candidates still participate in overload resolution.
- [ ] Template vs non-template overloads.
- [ ] Function template specialization pitfalls.
- [ ] `const` member functions.
- [ ] cv-qualified member functions.
- [ ] ref-qualified member functions (`&`, `&&`).
- [ ] `static` member functions.
- [ ] `noexcept` in function types/version implications.
- [ ] Return by value/reference/pointer.
- [ ] Returning references safely.
- [ ] `[[nodiscard]]` later.
- [ ] Variadic C-style functions only as legacy awareness; prefer variadic templates.
- [ ] Recursive calls and tail-call optimization as non-guaranteed implementation detail.

### Lab

Build deliberately ambiguous overload sets and explain every viable candidate and ranking.

---

## 2.7 Classes and object model

- [ ] Class vs struct default access/inheritance difference only.
- [ ] Access control.
- [ ] Data members.
- [ ] Static data members.
- [ ] Member functions.
- [ ] Nested types.
- [ ] Friends.
- [ ] Constructors.
- [ ] Delegating constructors.
- [ ] Converting constructors.
- [ ] `explicit` constructors.
- [ ] Destructor.
- [ ] Copy constructor/assignment.
- [ ] Move constructor/assignment.
- [ ] Member initialization order.
- [ ] Object slicing.
- [ ] Empty Base Optimization awareness.
- [ ] `[[no_unique_address]]` later.
- [ ] Empty class size.
- [ ] Alignment/padding.
- [ ] `this` pointer.
- [ ] `mutable`.
- [ ] `static` members.
- [ ] Nested/local classes awareness.
- [ ] Bit-fields and their restrictions.

---

## 2.8 Inheritance and runtime polymorphism

- [ ] Public/protected/private inheritance semantics.
- [ ] Is-a vs implementation reuse.
- [ ] Virtual functions.
- [ ] Pure virtual functions.
- [ ] Abstract classes.
- [ ] Virtual destructor rule.
- [ ] Override/final.
- [ ] Covariant return types awareness.
- [ ] Dynamic dispatch.
- [ ] Dispatch during construction/destruction.
- [ ] Multiple inheritance basics.
- [ ] Virtual inheritance and diamond problem awareness.
- [ ] Object layout/vptr/vtable as implementation model, not standard guarantee.
- [ ] RTTI.
- [ ] `dynamic_cast`.
- [ ] `typeid`.
- [ ] Slicing and polymorphic copying problem.
- [ ] NVI (Non-Virtual Interface) pattern awareness.

### Lab

Inspect a small hierarchy in memory and assembly while clearly labeling ABI-specific observations as implementation details.

---

## 2.9 Lifetime, storage duration and RAII

- [ ] Automatic storage duration.
- [ ] Static storage duration.
- [ ] Thread storage duration.
- [ ] Dynamic storage duration.
- [ ] Object lifetime beginning.
- [ ] Object lifetime ending.
- [ ] Temporary lifetime.
- [ ] Lifetime extension by references.
- [ ] Cases where lifetime is **not** extended.
- [ ] Dangling pointer/reference.
- [ ] Use-after-free.
- [ ] Use-after-scope.
- [ ] Placement new.
- [ ] Explicit destructor call awareness.
- [ ] Reuse of storage.
- [ ] `std::launder` concept and rare use case.
- [ ] Destruction order.
- [ ] RAII.
- [ ] Ownership vs observation.
- [ ] Resource handles other than memory: fd, mutex, socket, file, GPU handle later.

### Lab

Create a lifetime “bug zoo” and detect issues with ASan/UBSan where applicable.

---

## 2.10 Memory management fundamentals

- [ ] `new` expression vs allocation function `operator new`.
- [ ] `delete` expression vs `operator delete`.
- [ ] Array new/delete.
- [ ] Placement new.
- [ ] Matching allocation/deallocation.
- [ ] Custom `operator new/delete` awareness.
- [ ] Alignment-aware allocation awareness.
- [ ] `std::bad_alloc`.
- [ ] `new (std::nothrow)` awareness.
- [ ] Raw ownership as a smell in modern interfaces.
- [ ] Smart pointers later in Scott.
- [ ] Allocator model later in STL section.
- [ ] Arena/pool allocators later in performance curriculum, but language/API concepts begin here.

---

## 2.11 Exceptions and error safety

- [ ] `throw`, `try`, `catch`.
- [ ] Stack unwinding.
- [ ] Catch by value vs reference.
- [ ] `throw;` rethrow.
- [ ] Exception object lifetime.
- [ ] Destructors during unwinding.
- [ ] Destructors should generally not emit exceptions.
- [ ] `std::terminate` scenarios.
- [ ] `noexcept` and conditional `noexcept`.
- [ ] Basic guarantee.
- [ ] Strong guarantee.
- [ ] No-throw guarantee.
- [ ] Exception-neutral generic code.
- [ ] RAII as exception-safety foundation.
- [ ] Copy-and-swap as an educational pattern, not automatic default.
- [ ] Exceptions vs error codes vs `optional`/`expected` (modern sections later).

---

## 2.12 Casts and type conversions

- [ ] `static_cast`.
- [ ] `dynamic_cast`.
- [ ] `const_cast`.
- [ ] `reinterpret_cast`.
- [ ] C-style cast decomposition and why it hides intent.
- [ ] Numeric narrowing.
- [ ] Pointer conversions.
- [ ] Base/derived conversions.
- [ ] `std::bit_cast` later as safe bitwise representation conversion for suitable types.
- [ ] Strict aliasing/type-access rules at awareness level; performance curriculum will deepen.

---

## 2.13 Undefined, unspecified and implementation-defined behavior

- [ ] Difference between undefined behavior, unspecified behavior and implementation-defined behavior.
- [ ] Signed integer overflow.
- [ ] Invalid shifts.
- [ ] Out-of-bounds access.
- [ ] Use-after-lifetime.
- [ ] Dangling references/views.
- [ ] Uninitialized reads.
- [ ] Null dereference.
- [ ] Invalid downcast.
- [ ] Double delete.
- [ ] Mismatched allocation/deallocation.
- [ ] Data races (deep later).
- [ ] Invalidated iterators.
- [ ] Misaligned access.
- [ ] `reinterpret_cast` abuse.
- [ ] Modifying truly const objects through `const_cast`.
- [ ] Sequence/order hazards.
- [ ] Why “it works with -O0” proves nothing.

---

# 3. Scott Meyers audit — all 42 items, individually mandatory

The item list below is a **coverage checklist**. Every item gets its own mastery unit. Some items naturally require multiple labs and multiple videos.

## Block A — Type Deduction

### Item 1 — Understand template type deduction

- [ ] `ParamType = T` by value.
- [ ] `ParamType = T&`.
- [ ] `ParamType = const T&`.
- [ ] Pointer parameters.
- [ ] Forwarding-reference case `T&&` with deduction.
- [ ] Reference stripping during deduction.
- [ ] Top-level cv dropping for by-value parameters.
- [ ] Low-level cv preservation through pointers/references.
- [ ] Array-to-pointer decay for by-value parameters.
- [ ] Array extent preservation through reference parameters.
- [ ] Function-to-pointer decay for by-value parameters.
- [ ] Function type preservation through references.
- [ ] Predict both deduced `T` **and** final parameter type.

**Required lab:** 100-case `static_assert(std::is_same_v<...>)` deduction matrix.

### Item 2 — Understand `auto` type deduction

- [ ] Relationship to template deduction.
- [ ] `auto` by value.
- [ ] `auto&`.
- [ ] `const auto&`.
- [ ] `auto&&` and forwarding-reference behavior.
- [ ] Top-level cv dropping.
- [ ] Array/function decay.
- [ ] Brace-initializer special case.
- [ ] Difference between `auto x = {1,2}` and template deduction from braced init.
- [ ] Modern interactions with structured bindings later.

### Item 3 — Understand `decltype`

- [ ] Unparenthesized id-expression/member-access special rule.
- [ ] General expression rule.
- [ ] lvalue → `T&`.
- [ ] xvalue → `T&&`.
- [ ] prvalue → `T`.
- [ ] `decltype(x)` vs `decltype((x))`.
- [ ] `decltype(auto)` motivation.
- [ ] Return-type preservation.
- [ ] Parentheses changing return type and potentially creating dangling references.

### Item 4 — Know how to view deduced types

- [ ] IDE display.
- [ ] Compiler diagnostic trick.
- [ ] `static_assert`/traits.
- [ ] Runtime type-name limitations.
- [ ] Name mangling/demangling awareness.
- [ ] Why `typeid(T).name()` may lose cv/ref information depending on usage.

**Block gate:** 100 mixed deduction questions, >=90% closed-book.

---

## Block B — `auto`

### Item 5 — Prefer `auto` to explicit type declarations

- [ ] Avoid uninitialized variables.
- [ ] Iterator verbosity.
- [ ] Closure types cannot be named directly.
- [ ] Correct type when APIs change.
- [ ] Accidental conversion from wrong explicit type.
- [ ] `unordered_map` key is `const Key` in `value_type` — iteration-copy trap.
- [ ] Readability trade-off.
- [ ] When explicit type better communicates semantics.

### Item 6 — Use the explicitly typed initializer idiom when `auto` deduces undesired types

- [ ] Proxy types.
- [ ] `std::vector<bool>::reference` classic example.
- [ ] Expression-template/proxy concept.
- [ ] Hidden/lazy conversion.
- [ ] Lifetime of proxy operands.
- [ ] Forcing materialization with an explicit target type.
- [ ] Recognizing APIs that return proxy objects intentionally.

**Required lab:** build a tiny proxy type that becomes dangerous when captured by `auto`.

---

## Block C — Moving to Modern C++

### Item 7 — Distinguish between `()` and `{}` when creating objects

- [ ] Direct initialization with parentheses.
- [ ] List initialization.
- [ ] Copy-list initialization.
- [ ] Narrowing prevention.
- [ ] Most-vexing parse avoidance.
- [ ] `std::initializer_list` preferential overload matching.
- [ ] `vector(size, value)` vs `vector{elements}`.
- [ ] Constructor resolution surprises.
- [ ] Empty braces and default construction.
- [ ] Aggregate interactions.
- [ ] C++17/20 aggregate evolution later.

### Item 8 — Prefer `nullptr` to `0` and `NULL`

- [ ] `std::nullptr_t`.
- [ ] Null pointer conversion.
- [ ] Integral overload ambiguity.
- [ ] Template deduction differences.
- [ ] Generic forwarding behavior.
- [ ] Boolean-context behavior.

### Item 9 — Prefer alias declarations to `typedef`s

- [ ] `using Name = Type`.
- [ ] Readability for function pointers.
- [ ] Alias templates.
- [ ] Dependent types.
- [ ] Interaction with traits and `_t` aliases.
- [ ] Why alias templates simplify metaprogramming.

### Item 10 — Prefer scoped enums to unscoped enums

- [ ] Name pollution.
- [ ] Implicit conversion to integral types.
- [ ] Explicit conversion when needed.
- [ ] Underlying type.
- [ ] Forward declaration.
- [ ] ABI/serialization caution around underlying representation.
- [ ] `std::to_underlying` later (C++23).

### Item 11 — Prefer deleted functions to private undefined ones

- [ ] `= delete` gives compile-time diagnostics.
- [ ] Deleting copy/move operations.
- [ ] Deleting dangerous overloads.
- [ ] Access checking vs deleted-function diagnosis.
- [ ] Deleted template specializations/overloads.
- [ ] Deleted candidates still participate in overload resolution.

### Item 12 — Declare overriding functions `override`

- [ ] Signature mismatch.
- [ ] Missing `const`.
- [ ] Reference qualifiers.
- [ ] Parameter type mismatch.
- [ ] Base function renamed/changed.
- [ ] `override` catches errors.
- [ ] `final` awareness.
- [ ] `virtual` + `override` style discussion.

### Item 13 — Prefer `const_iterator`s to `iterator`s

- [ ] Mutation intent.
- [ ] `cbegin`/`cend`.
- [ ] Generic algorithm interaction.
- [ ] Insertion/erase positions using const_iterator where supported.
- [ ] Historical C++98 limitations vs modern library.

### Item 14 — Declare functions `noexcept` if they will not emit exceptions

- [ ] `noexcept` as contract.
- [ ] Termination on escaping exception.
- [ ] Conditional `noexcept`.
- [ ] `noexcept(expression)` operator.
- [ ] Move constructors and containers.
- [ ] `std::move_if_noexcept`.
- [ ] Function-type implications in newer standards.
- [ ] Do not mark `noexcept` casually when dependencies may throw.

**Required lab:** vector relocation with throwing vs `noexcept` move.

### Item 15 — Use `constexpr` whenever possible

- [ ] `constexpr` objects.
- [ ] `constexpr` functions.
- [ ] Compile-time eligibility vs guarantee of compile-time evaluation.
- [ ] Literal types.
- [ ] Version-by-version relaxation.
- [ ] `consteval`/`constinit` later.
- [ ] Compile-time validation.
- [ ] Performance is not the only motivation; stronger invariants/API capability matter.

### Item 16 — Make `const` member functions thread safe

- [ ] Logical vs bitwise constness.
- [ ] `mutable` synchronization members.
- [ ] Lazy caching.
- [ ] Data races despite `const`.
- [ ] Mutex solution.
- [ ] Atomic solution when semantics permit.
- [ ] Multiple fields/invariants requiring a lock rather than independent atomics.

### Item 17 — Understand special member function generation

- [ ] Default constructor generation conditions.
- [ ] Destructor generation.
- [ ] Copy constructor generation/deletion.
- [ ] Copy assignment generation/deletion.
- [ ] Move constructor generation/suppression/deletion.
- [ ] Move assignment generation/suppression/deletion.
- [ ] User-declared destructor suppressing implicit moves in classic rules.
- [ ] Member/base type effects.
- [ ] `= default`.
- [ ] `= delete`.
- [ ] Triviality.
- [ ] Rule of Zero.
- [ ] Rule of Five.
- [ ] Polymorphic base-class special-member considerations.

**Required lab:** matrix of classes with `std::is_*constructible/assignable` traits.

---

## Block D — Smart Pointers

### Item 18 — Use `std::unique_ptr` for exclusive-ownership resource management

- [ ] Exclusive ownership.
- [ ] Move-only semantics.
- [ ] Default deleter.
- [ ] Stateful/stateless custom deleters.
- [ ] `unique_ptr<T, D>` type includes deleter type.
- [ ] Empty-base/size optimization as implementation technique awareness.
- [ ] `unique_ptr<T[]>`.
- [ ] `make_unique`.
- [ ] Release/reset/swap/get.
- [ ] Observer access vs ownership transfer.
- [ ] Passing by value when transferring ownership.
- [ ] Passing by reference/pointer when borrowing.
- [ ] Incomplete-type/PImpl considerations.
- [ ] Converting `unique_ptr<Derived>` to `unique_ptr<Base>` and virtual-destructor implications.

**Build:** educational `UniquePtr<T>` supporting move, reset, release and custom deleter basics.

### Item 19 — Use `std::shared_ptr` for shared-ownership resource management

- [ ] Shared ownership semantics.
- [ ] Control block.
- [ ] Strong count.
- [ ] Weak count awareness.
- [ ] Object pointer vs control-block pointer conceptual distinction.
- [ ] Separate allocation vs `make_shared` co-allocation.
- [ ] Custom deleter stored in control block.
- [ ] Construction from raw pointer creates control block.
- [ ] Double-control-block catastrophe from constructing two shared_ptrs from same raw pointer.
- [ ] `enable_shared_from_this` purpose and misuse.
- [ ] Aliasing constructor concept.
- [ ] Atomicity of reference-count operations vs thread safety of pointed object.
- [ ] Shared ownership cost.
- [ ] Prefer clear ownership models over “use shared_ptr everywhere”.

**Build:** simplified reference-counted pointer and inspect allocation/refcount behavior.

### Item 20 — Use `std::weak_ptr` for `std::shared_ptr`-like pointers that can dangle

- [ ] Non-owning reference to shared control block.
- [ ] `expired()`.
- [ ] `lock()`.
- [ ] Race-safe acquisition concept through `lock()`.
- [ ] Breaking ownership cycles.
- [ ] Cache use case.
- [ ] Observer-list use case.
- [ ] Weak-count/control-block lifetime awareness.

### Item 21 — Prefer `std::make_unique` and `std::make_shared` to direct use of `new`

- [ ] Exception-safety motivation.
- [ ] Reduced repetition.
- [ ] `make_shared` one-allocation advantage.
- [ ] `make_shared` object/control-block co-allocation.
- [ ] Weak references may keep combined allocation alive after object destruction.
- [ ] Custom deleter limitation.
- [ ] Private constructor/factory access considerations.
- [ ] Very large object/allocation trade-offs.

### Item 22 — When using PImpl, define special member functions in the implementation file

- [ ] Incomplete type.
- [ ] Why default deleter needs complete type at destruction point.
- [ ] Out-of-line destructor.
- [ ] Move operations with PImpl.
- [ ] Compile-time dependency reduction.
- [ ] ABI stability motivation.
- [ ] Cost of indirection/allocation.

**Block gate:** Given a nontrivial ownership graph, annotate every edge as owner/observer/shared/borrowed and justify every pointer/reference choice.

---

## Block E — Rvalue References, Move Semantics, Perfect Forwarding

### Item 23 — Understand `std::move` and `std::forward`

- [ ] Both are casts/utilities, not moving operations themselves.
- [ ] `std::move` casts toward rvalue/xvalue category.
- [ ] Move occurs only if an appropriate overload exists.
- [ ] Moving from `const` often selects copy because move constructors typically need non-const rvalue.
- [ ] Moved-from object remains valid but state is generally unspecified unless type documents more.
- [ ] `std::forward<T>` conditionally preserves original value category.
- [ ] Misusing forward on non-forwarding contexts.

### Item 24 — Distinguish universal/forwarding references from rvalue references

- [ ] `T&&` with type deduction vs concrete `Type&&`.
- [ ] `auto&&` deduction contexts.
- [ ] `const T&&` is not a forwarding reference.
- [ ] Class-template parameter already known vs function-template deduction.
- [ ] Reference collapsing behind forwarding references.
- [ ] Generic lambda `auto&&`.

### Item 25 — Use `std::move` on rvalue references and `std::forward` on forwarding references

- [ ] Named rvalue references are lvalue expressions.
- [ ] Last-use rule.
- [ ] Forward exactly when passing onward.
- [ ] Forward each parameter with its corresponding template type.
- [ ] Returning by value and why explicit `std::move` can inhibit NRVO.
- [ ] Moving members from rvalue-qualified functions.

### Item 26 — Avoid overloading on forwarding references

- [ ] Greedy matching.
- [ ] Lvalue of unexpected type binding better than intended overload.
- [ ] Forwarding constructor hijacking copy construction.
- [ ] Derived-to-base surprises.
- [ ] Overload resolution hazards.
- [ ] API maintainability cost.

### Item 27 — Familiarize yourself with alternatives to overloading on forwarding references

- [ ] Abandon overloading / use distinct names.
- [ ] Pass `const T&`.
- [ ] Pass by value for copyable/movable types.
- [ ] Tag dispatch.
- [ ] Constrain accepted types.
- [ ] `enable_if`/SFINAE historically.
- [ ] Concepts/requires in modern C++.

### Item 28 — Understand reference collapsing

- [ ] `& + & -> &`.
- [ ] `& + && -> &`.
- [ ] `&& + & -> &`.
- [ ] `&& + && -> &&`.
- [ ] Template deduction context.
- [ ] `auto&&`.
- [ ] `typedef`/alias contexts.
- [ ] `decltype` contexts.
- [ ] Why this enables perfect forwarding.

### Item 29 — Assume move operations are not present, not cheap, and not used

- [ ] Type may not declare move operations.
- [ ] Copy may handle rvalues.
- [ ] `const` blocks typical move overloads.
- [ ] Small/trivial types may gain nothing.
- [ ] SSO/string implementation effects.
- [ ] Containers may move cheaply while elements do not, or vice versa.
- [ ] `noexcept` may affect container relocation choice.
- [ ] Copy elision can eliminate both copy and move.
- [ ] Measure rather than fetishize `std::move`.

### Item 30 — Familiarize yourself with perfect-forwarding failure cases

- [ ] Braced initializers.
- [ ] `0`/`NULL` as null pointer constants.
- [ ] Declaration-only static const integral members / ODR-era issue awareness.
- [ ] Overloaded function names.
- [ ] Function templates as arguments.
- [ ] Bit-fields cannot bind as ordinary non-const references in the needed way.
- [ ] API redesign when forwarding cannot represent the call cleanly.

## Mandatory Josuttis move-semantics expansion

Beyond Scott, master:

- [ ] Motivation and performance model of moves.
- [ ] Self-move and self-move assignment behavior/design.
- [ ] Member move initialization.
- [ ] Move and overload resolution.
- [ ] xvalues in depth.
- [ ] `decltype` of expressions in move contexts.
- [ ] Ref-qualified member functions.
- [ ] Return type of getters (`T`, `T&`, `const T&`, `T&&`) and lifetime consequences.
- [ ] Move semantics in polymorphic class hierarchies.
- [ ] `const&&` and why it is unusual.
- [ ] “Perfect passing” vs perfect forwarding concepts.
- [ ] Forwarding references in APIs that are not actually forwarding.
- [ ] Perfect returning / `decltype(auto)`.
- [ ] Move semantics in lambdas.
- [ ] Move semantics in range-based for.
- [ ] Move-only standard-library types: streams, threads, unique_ptr.
- [ ] `std::move_iterator`.
- [ ] Moving algorithms.
- [ ] Remove algorithms and move semantics.
- [ ] Strings/containers and allocator-dependent move behavior.
- [ ] `std::shared_ptr` move behavior.
- [ ] `std::pair`/tuple move behavior.
- [ ] `std::optional` move behavior.

**Block gate:** Whiteboard value categories/reference collapsing; write a correct forwarding wrapper from memory; diagnose five examples where `std::move` still copies.

---

## Block F — Lambdas

### Item 31 — Avoid default capture modes

- [ ] `[&]` maintenance/lifetime hazards.
- [ ] `[=]` maintenance/lifetime hazards.
- [ ] `this` historically captured, not a snapshot of every member.
- [ ] Dangling `this` when closure outlives object.
- [ ] Static-storage/global variables not captured as locals.
- [ ] Explicit captures improve reviewability.
- [ ] Modern `[*this]` copy semantics later.

### Item 32 — Use init capture to move objects into closures

- [ ] Generalized lambda capture.
- [ ] Move-only state.
- [ ] Capture expressions.
- [ ] Closure member lifetime.
- [ ] Ownership transfer into callback.
- [ ] Pre-C++14 workaround awareness only.

### Item 33 — Use `decltype` on `auto&&` parameters to `std::forward` them

- [ ] Generic lambda parameters.
- [ ] `auto&&` as forwarding reference.
- [ ] `decltype(param)` as forwarding type.
- [ ] Preserve lvalue/rvalue category.
- [ ] Multiple parameters.

### Item 34 — Prefer lambdas to `std::bind`

- [ ] Readability.
- [ ] Argument binding clarity.
- [ ] Overloaded function handling.
- [ ] Evaluation timing.
- [ ] Perfect forwarding limitations.
- [ ] Placeholder opacity.
- [ ] Generated-type/compiler optimization considerations.

---

## Block G — Concurrency API Preview from Scott

These are mastered to modern-C++ API depth here and then revisited much more deeply in Curriculum 02.

### Item 35 — Prefer task-based programming to thread-based

- [ ] Return values through futures.
- [ ] Exception propagation.
- [ ] Thread management abstraction.
- [ ] Scheduler freedom.
- [ ] Cases needing explicit thread identity/priority/affinity later.

### Item 36 — Specify `std::launch::async` if asynchronicity is essential

- [ ] Default policy may be `async`, `deferred`, or implementation choice.
- [ ] Deferred execution.
- [ ] `wait_for`/status behavior awareness.
- [ ] Destructor/wait semantics awareness.
- [ ] Why explicit policy matters to correctness/performance assumptions.

### Item 37 — Make `std::thread`s unjoinable on all paths

- [ ] Joinable definition.
- [ ] Destructor of joinable `std::thread` terminates.
- [ ] Exception paths.
- [ ] Join vs detach consequences.
- [ ] RAII thread ownership.
- [ ] C++20 `std::jthread` comparison later.

### Item 38 — Be aware of varying thread-handle destructor behavior

- [ ] `std::thread` destructor termination if joinable.
- [ ] Future destructor behavior can depend on creation/source.
- [ ] Avoid assuming all asynchronous handles behave alike.

### Item 39 — Consider `void` futures for one-shot event communication

- [ ] Promise/future one-shot signal.
- [ ] Condition-variable alternative.
- [ ] Shared future awareness.
- [ ] One-shot nature and ownership.

### Item 40 — Use `std::atomic` for concurrency, `volatile` for special memory

- [ ] `volatile` does not make operations atomic.
- [ ] `volatile` does not establish inter-thread happens-before.
- [ ] Atomic read-modify-write.
- [ ] Compiler optimization constraints of volatile are not synchronization semantics.
- [ ] Memory-mapped I/O/special-memory motivation at awareness level.

---

## Block H — Tweaks

### Item 41 — Consider pass by value for copyable parameters that are cheap to move and always copied

- [ ] `const T&` + copy inside.
- [ ] Overload pair (`const T&`, `T&&`).
- [ ] By-value + move into member.
- [ ] Lvalue caller cost.
- [ ] Rvalue caller cost.
- [ ] Slicing risk for polymorphic types.
- [ ] Move-assignment cost may differ from move-construction.
- [ ] Exception behavior.
- [ ] Parameter only “sometimes copied” changes the trade-off.
- [ ] Large/expensive-to-move types.

### Item 42 — Consider emplacement instead of insertion

- [ ] `emplace_back`/`emplace` construct in destination.
- [ ] It does not universally mean fewer operations.
- [ ] Explicit constructors can be invoked through emplacement.
- [ ] API may accept argument combinations `push` would reject.
- [ ] Resource-management safety considerations.
- [ ] Associative-container emplacement variants.
- [ ] `try_emplace` later.
- [ ] Measure real effects; do not cargo-cult emplace.

---

# 4. Template and generic-programming mastery — beyond Scott

Primary source: **C++ Templates: The Complete Guide, 2nd Edition** plus cppreference.

## 4.1 Function templates

- [ ] Basic deduction.
- [ ] Multiple template parameters.
- [ ] Default template arguments.
- [ ] Overloading function templates.
- [ ] Template/non-template overload resolution.
- [ ] Return-type deduction issues.
- [ ] Explicit template arguments.

## 4.2 Class templates

- [ ] Class-template definition/use.
- [ ] Instantiation on demand.
- [ ] Member templates.
- [ ] Friend declarations.
- [ ] Full specialization.
- [ ] Partial specialization.
- [ ] Default template arguments.
- [ ] Alias templates.
- [ ] CTAD.
- [ ] User-defined deduction guides.
- [ ] Templated aggregates.

## 4.3 Non-type template parameters (NTTPs)

- [ ] Integral/enum values.
- [ ] Pointers/references historical constraints awareness.
- [ ] `auto` NTTPs.
- [ ] Structural types in newer standards at practical level.
- [ ] Compile-time configuration use cases.

## 4.4 Variadic templates

- [ ] Parameter packs.
- [ ] Pack expansion locations.
- [ ] Recursive variadic pattern awareness.
- [ ] Fold expressions.
- [ ] `sizeof...`.
- [ ] Variadic inheritance/mixins awareness.

## 4.5 Dependent names and lookup

- [ ] Dependent vs non-dependent names.
- [ ] Why `typename` is required.
- [ ] Why `template` disambiguator is required.
- [ ] `this->` in dependent base classes.
- [ ] Two-phase lookup model.
- [ ] ADL with templates.
- [ ] Point of instantiation awareness.
- [ ] Common “works on one compiler, fails on another” historical portability traps.

## 4.6 Specialization and instantiation

- [ ] Full function-template specialization and why overloads are often preferable.
- [ ] Full class specialization.
- [ ] Partial class specialization.
- [ ] Variable-template specialization.
- [ ] Explicit instantiation declaration (`extern template`).
- [ ] Explicit instantiation definition.
- [ ] Code-bloat/build-time motivations.

## 4.7 SFINAE and constraints

- [ ] Substitution failure vs hard error.
- [ ] Immediate context at practical level.
- [ ] `std::enable_if`.
- [ ] Detection idiom / `void_t`.
- [ ] Traits-based dispatch.
- [ ] Tag dispatch.
- [ ] Why concepts are generally clearer for new C++20 code.
- [ ] Read legacy SFINAE even if you prefer concepts.

## 4.8 Type traits

- [ ] Primary category traits.
- [ ] Composite traits.
- [ ] Property traits.
- [ ] Type transformations.
- [ ] `_v` and `_t` helper aliases.
- [ ] `decay`.
- [ ] `remove_cvref`.
- [ ] `common_type`/`common_reference` awareness.
- [ ] `is_invocable` family.
- [ ] `invoke_result`.
- [ ] Traits driving `if constexpr`/concepts.

## 4.9 Metaprogramming

- [ ] Compile-time values/types.
- [ ] Integral constants.
- [ ] Recursive instantiation awareness.
- [ ] `constexpr` replacing some template metaprogramming.
- [ ] `if constexpr`.
- [ ] Compile-time complexity/build-time cost.
- [ ] Template diagnostics and maintainability.
- [ ] Avoid cleverness without value.

## 4.10 Generic-library design

- [ ] Requirements on template parameters.
- [ ] Concepts as executable/documented requirements.
- [ ] Perfect forwarding where justified.
- [ ] Customization points awareness.
- [ ] ADL-based customization.
- [ ] Hidden friends.
- [ ] Policy-based design.
- [ ] CRTP.
- [ ] Mixins.
- [ ] Type erasure as an alternative to templates.

**Template gate:** implement a small generic library using function/class templates, traits, variadics and concepts; diagnose dependent-name and overload-resolution failures without searching first.

---

# 5. Standard Library / STL mastery

Do not reduce STL knowledge to “I know vector/map”. For every container/algorithm, learn complexity, iterator invalidation, exception behavior, allocation behavior and cache implications at a practical level.

## 5.1 Sequence containers

- [ ] `std::array`.
- [ ] `std::vector`.
- [ ] `std::deque`.
- [ ] `std::list`.
- [ ] `std::forward_list`.

For each:
- [ ] Memory layout model.
- [ ] Complexity guarantees.
- [ ] Iterator/reference invalidation.
- [ ] Growth/insertion/erase behavior.
- [ ] Allocation behavior.
- [ ] Exception guarantees.
- [ ] Move/copy implications.
- [ ] Typical cache behavior.

**Mandatory build:** educational `Vector<T>` using raw storage, placement construction, destruction, growth and exception safety.

## 5.2 Associative containers

- [ ] `set` / `multiset`.
- [ ] `map` / `multimap`.
- [ ] Comparator strict-weak-order requirement.
- [ ] Transparent comparators / heterogeneous lookup awareness.
- [ ] Node handles (`extract`).
- [ ] `merge`.
- [ ] `try_emplace`.
- [ ] `insert_or_assign`.

## 5.3 Unordered containers

- [ ] `unordered_set` / `unordered_map` families.
- [ ] Hash/equality contract.
- [ ] Buckets.
- [ ] Load factor.
- [ ] Rehash.
- [ ] Iterator invalidation.
- [ ] Adversarial/poor hash awareness.
- [ ] Reserve/rehash API.

## 5.4 Container adaptors

- [ ] `stack`.
- [ ] `queue`.
- [ ] `priority_queue`.
- [ ] Understand underlying-container parameterization.

## 5.5 Strings and views

- [ ] `std::string` ownership.
- [ ] Capacity/SSO awareness as implementation detail.
- [ ] Iterator/reference invalidation.
- [ ] `string_view` non-ownership.
- [ ] `string_view` dangling hazards.
- [ ] Substring/view operations.
- [ ] `char_traits` awareness.

**Mandatory lab:** string_view lifetime bug zoo.

## 5.6 Iterators

- [ ] Input/output/forward/bidirectional/random-access categories.
- [ ] Contiguous iterator concept in modern C++.
- [ ] Iterator traits.
- [ ] `begin/end`, `cbegin/cend`.
- [ ] Reverse iterators.
- [ ] Move iterators.
- [ ] Insert iterators.
- [ ] Stream iterators awareness.
- [ ] Sentinel model in ranges.
- [ ] Iterator invalidation tables memorized conceptually, not mechanically.

## 5.7 Algorithms

- [ ] Non-modifying sequence algorithms.
- [ ] Modifying algorithms.
- [ ] Partitioning.
- [ ] Sorting/partial sorting.
- [ ] Binary search family.
- [ ] Set algorithms.
- [ ] Heap algorithms.
- [ ] Min/max.
- [ ] Numeric algorithms.
- [ ] Remove/erase idiom and modern `erase`/`erase_if`.
- [ ] Predicates and strict weak ordering.
- [ ] Lambdas as predicates/projections.
- [ ] Parallel execution policies awareness and safety constraints.

## 5.8 Callable vocabulary

- [ ] Function pointers.
- [ ] Member pointers.
- [ ] Functors.
- [ ] Lambdas.
- [ ] `std::function` type erasure and allocation/cost awareness.
- [ ] `std::bind` legacy understanding.
- [ ] `std::invoke`.
- [ ] `std::mem_fn` awareness.
- [ ] `std::move_only_function` in C++23.

## 5.9 Product/sum/optional vocabulary types

- [ ] `pair`.
- [ ] `tuple`.
- [ ] structured bindings.
- [ ] `optional`.
- [ ] `variant`.
- [ ] `visit`.
- [ ] `monostate`.
- [ ] `any`.
- [ ] `expected` in C++23.
- [ ] When each communicates API semantics better than sentinel values/raw unions.

## 5.10 Smart pointers and allocator-aware library

- [ ] `allocator` model.
- [ ] `allocator_traits`.
- [ ] Propagation traits awareness.
- [ ] Stateful allocator implications.
- [ ] Allocator effects on container move/swap behavior awareness.
- [ ] `std::pmr::memory_resource`.
- [ ] `monotonic_buffer_resource`.
- [ ] `polymorphic_allocator`.
- [ ] Scoped allocator awareness.

## 5.11 Utility/system library

- [ ] `chrono` fundamentals.
- [ ] `filesystem`.
- [ ] `random` engines vs distributions.
- [ ] `numeric` algorithms.
- [ ] `bitset`.
- [ ] `<bit>` utilities in newer standards.
- [ ] `span`.
- [ ] `mdspan` later.
- [ ] `source_location`.
- [ ] `format`/`print`.
- [ ] `stacktrace`.
- [ ] `regex` awareness; not an interview priority unless role needs it.
- [ ] iostream state/RAII/manipulators at working level.

**STL gate:** Given an unfamiliar workload, choose a container/algorithm and justify complexity, invalidation, allocation, lifetime and cache behavior.

---

# 6. C++17 — systematic coverage

Use Josuttis C++17 guide + cppreference. Do not learn only the headline features.

## 6.1 Language

- [ ] Structured bindings.
- [ ] Structured binding lifetime/reference behavior.
- [ ] `if`/`switch` with initializer.
- [ ] `if constexpr`.
- [ ] Fold expressions.
- [ ] CTAD.
- [ ] Deduction guides.
- [ ] Inline variables.
- [ ] Guaranteed copy elision in specified prvalue cases.
- [ ] Prvalue materialization model change awareness.
- [ ] `noexcept` as part of function type.
- [ ] Nested namespace syntax.
- [ ] `constexpr` lambda.
- [ ] Lambda capture of `*this`.
- [ ] Attributes: `[[nodiscard]]`, `[[maybe_unused]]`, `[[fallthrough]]`.
- [ ] Aggregate/base-class changes at practical level.
- [ ] `auto` NTTP.
- [ ] Variadic using-declarations awareness.

## 6.2 Library

- [ ] `optional`.
- [ ] `variant`.
- [ ] `any`.
- [ ] `string_view`.
- [ ] `filesystem`.
- [ ] `byte`.
- [ ] `invoke`.
- [ ] `apply`.
- [ ] `make_from_tuple` awareness.
- [ ] `from_chars` / `to_chars`.
- [ ] `scoped_lock`.
- [ ] `shared_mutex`/`shared_lock` availability context.
- [ ] Parallel algorithms/execution policies.
- [ ] `pmr` polymorphic memory resources.
- [ ] Node handles for associative containers.
- [ ] `try_emplace` / `insert_or_assign`.
- [ ] `clamp`.
- [ ] `gcd` / `lcm` awareness.
- [ ] `hardware_destructive_interference_size` / constructive interference size awareness.
- [ ] `launder` awareness.

**C++17 gate:** build a small application using structured bindings, variant/visit, optional, string_view, filesystem, CTAD and pmr deliberately — then identify all non-owning lifetimes.

---

# 7. C++20 — systematic coverage

Use Josuttis C++20 guide + cppreference.

## 7.1 Concepts and constraints

- [ ] Concept definition.
- [ ] Requires-clause.
- [ ] Requires-expression.
- [ ] Simple requirement.
- [ ] Type requirement.
- [ ] Compound requirement.
- [ ] Nested requirement.
- [ ] Abbreviated function templates.
- [ ] Constrained `auto`.
- [ ] Constraint normalization/subsumption at practical overload-resolution level.
- [ ] Standard concepts (`same_as`, `convertible_to`, integral concepts, invocable/predicate/regular, iterator concepts, etc.) at working level.
- [ ] Replace legacy SFINAE example with concepts.

## 7.2 Ranges

- [ ] Range vs iterator/sentinel.
- [ ] Views are generally non-owning/lazy.
- [ ] View lifetime hazards.
- [ ] Borrowed ranges awareness.
- [ ] Dangling handling.
- [ ] Range algorithms.
- [ ] Projections.
- [ ] Common views: transform, filter, take, drop, reverse, split, join awareness.
- [ ] Pipe syntax.
- [ ] Iterator category/concept interactions.
- [ ] Performance/laziness implications.

## 7.3 Coroutines

- [ ] Coroutine transformation mental model.
- [ ] Coroutine frame.
- [ ] Promise type.
- [ ] `co_await`.
- [ ] Awaitable/awaiter protocol.
- [ ] `await_ready` / `await_suspend` / `await_resume`.
- [ ] `co_yield`.
- [ ] `co_return`.
- [ ] Initial/final suspend.
- [ ] Lifetime of frame.
- [ ] Allocation/elision awareness.
- [ ] Exceptions in coroutines.
- [ ] Build a tiny educational task/generator-like coroutine.

## 7.4 Modules

- [ ] Module interface unit.
- [ ] Module implementation unit.
- [ ] Import/export.
- [ ] Global module fragment awareness.
- [ ] Header units awareness.
- [ ] Build-system/toolchain maturity considerations.
- [ ] Modules do not automatically solve ABI/versioning.

## 7.5 Language additions

- [ ] Three-way comparison `<=>`.
- [ ] Defaulted comparisons.
- [ ] Comparison categories.
- [ ] Designated initializers and restrictions.
- [ ] `consteval`.
- [ ] `constinit`.
- [ ] Expanded `constexpr` capabilities.
- [ ] Templated lambdas.
- [ ] `char8_t`.
- [ ] `[[no_unique_address]]`.
- [ ] Aggregate initialization with parentheses awareness.
- [ ] Likely/unlikely attributes awareness.

## 7.6 Library additions

- [ ] `span`.
- [ ] `jthread`.
- [ ] `stop_token`/stop source/callback awareness.
- [ ] `semaphore`.
- [ ] `latch`.
- [ ] `barrier`.
- [ ] `atomic_ref`.
- [ ] Atomic wait/notify.
- [ ] `bit_cast`.
- [ ] `endian`.
- [ ] Bit operations (`popcount`, rotations, countl/countr, etc.).
- [ ] `source_location`.
- [ ] `format`.
- [ ] `starts_with`/`ends_with`.
- [ ] `erase`/`erase_if`.
- [ ] `ssize`.
- [ ] `to_array`.
- [ ] `midpoint`/`lerp` awareness.
- [ ] Calendar/time-zone additions at awareness level unless needed.
- [ ] `syncstream` awareness.
- [ ] `make_shared` array support awareness.

**C++20 gate:** use concepts + ranges + one coroutine + `span` + `jthread` in a coherent mini-project and explain all ownership/lifetime boundaries.

---

# 8. C++23 — systematic practical coverage

Use Josuttis C++23 guide + cppreference. Focus on features relevant to systems, API design and generic code, while still being aware of the broader release.

## 8.1 Language

- [ ] Explicit object parameter / “deducing this”.
- [ ] Recursive lambdas enabled by explicit object parameter pattern.
- [ ] `if consteval`.
- [ ] Static `operator()`.
- [ ] Static `operator[]`.
- [ ] Multidimensional subscript improvements.
- [ ] Range-for lifetime fixes.
- [ ] `auto(x)` / `auto{x}` decay-copy style use.
- [ ] Extended floating-point NTTP/constexpr-related awareness where supported.
- [ ] C++23 constexpr relaxations at practical level.

## 8.2 Library

- [ ] `expected`.
- [ ] `unexpected`.
- [ ] Monadic operations on `expected`.
- [ ] Monadic operations on `optional`.
- [ ] `move_only_function`.
- [ ] `forward_like`.
- [ ] `mdspan`.
- [ ] `print` / `println`.
- [ ] `stacktrace`.
- [ ] `to_underlying`.
- [ ] `byteswap`.
- [ ] `unreachable` and the danger of lying to the optimizer.
- [ ] `out_ptr` / `inout_ptr` awareness for C interop.
- [ ] `spanstream` awareness.
- [ ] `string::contains` / `string_view::contains`.
- [ ] `ranges::to`.
- [ ] New ranges/views such as zip/adjacent/chunk/slide/stride/repeat/cartesian families at working awareness depending library support.
- [ ] Range fold algorithms.
- [ ] `std::generator`.
- [ ] Flat associative containers (`flat_map`, `flat_set`) availability/support awareness.
- [ ] Formatting/ranges/tuple improvements.

**C++23 gate:** redesign an older API using `expected`, `move_only_function`, `forward_like`, modern ranges and `mdspan` where each feature is justified; explain toolchain/library support before using it in production.

---

# 9. C++26 and post-C++23 awareness — do not let interviews surprise you

C++26-era features are **awareness-first**, because compiler/library support and interview expectations vary.

For the toolchains you actually use:

- [ ] Know how to check compiler language-standard support.
- [ ] Know feature-test macros (`__cpp_*`, library feature-test macros) conceptually.
- [ ] Track the current standard mode supported by GCC and Clang.
- [ ] Be aware of major new standard-library/concurrency/execution developments relevant to systems programming.
- [ ] Never claim production support without checking your actual compiler + standard library.

Do not spend disproportionate time memorizing brand-new features before mastering C++11–23 fundamentals.

---

# 10. ABI, linking, binary boundaries and build/toolchain mastery

This section is mandatory for senior C++ and architect-level interviews.

## 10.1 Compilation/linking

- [ ] Preprocessor output.
- [ ] Compilation to object file.
- [ ] Assembly generation.
- [ ] Linking.
- [ ] Static library.
- [ ] Shared library.
- [ ] Symbol table.
- [ ] Relocations awareness.
- [ ] Dynamic loader awareness.
- [ ] Name mangling.
- [ ] Demangling.
- [ ] ODR failures.
- [ ] Undefined symbols.
- [ ] Duplicate symbols.
- [ ] Link order issues awareness.
- [ ] Visibility attributes/toolchain controls awareness.

## 10.2 ABI

- [ ] What ABI means.
- [ ] Calling convention awareness.
- [ ] Name mangling.
- [ ] Class layout as ABI surface.
- [ ] Vtable/vptr ABI reality.
- [ ] Inline/template code across ABI boundaries.
- [ ] STL types across binary boundaries and toolchain/version concerns.
- [ ] Exception ABI concerns awareness.
- [ ] RTTI across DSOs awareness.
- [ ] PImpl for ABI insulation.
- [ ] Versioned APIs.
- [ ] Symbol visibility.
- [ ] Plugin interfaces and C ABI boundary option.

## 10.3 Build systems and compiler modes

- [ ] CMake fundamentals.
- [ ] Targets rather than global flags.
- [ ] PUBLIC/PRIVATE/INTERFACE dependencies.
- [ ] Include directories.
- [ ] Compile features / C++ standard selection.
- [ ] Debug vs release.
- [ ] Sanitizer builds.
- [ ] LTO awareness.
- [ ] PGO awareness.
- [ ] Warnings-as-errors trade-off.
- [ ] GCC vs Clang diagnostic differences.

## 10.4 Binary-tool lab

Build a small shared library and:

- inspect symbols with `nm`/`readelf`,
- inspect dependencies with `ldd`,
- inspect assembly with `objdump`,
- intentionally break ABI by changing class layout,
- then redesign with PImpl.

---

# 11. Debugging, sanitizers and failure diagnosis

A senior C++ engineer must be able to diagnose, not only write.

- [ ] Compile-time errors: read first meaningful diagnostic rather than last cascade.
- [ ] Template error reduction strategy.
- [ ] Debug build flags.
- [ ] gdb/lldb breakpoints.
- [ ] Conditional breakpoints.
- [ ] Watchpoints.
- [ ] Stack traces.
- [ ] Core dumps.
- [ ] Inspect locals/objects/vtables where useful.
- [ ] ASan use-after-free.
- [ ] ASan buffer overflow.
- [ ] ASan use-after-scope.
- [ ] UBSan signed overflow/misalignment/bad casts where detected.
- [ ] Leak detection.
- [ ] TSan data-race introduction only; deep use in Curriculum 02.
- [ ] Reproduce nondeterministic bugs with minimized test cases.
- [ ] Delta-debug/minimal-reproducer habit.
- [ ] Compiler Explorer for isolated compiler behavior.

**Gate:** Given ten seeded bugs, find root cause with evidence rather than guessing.

---

# 12. API design, const-correctness and ownership vocabulary

This remains C++-specific even before the later architecture curriculum.

- [ ] Value semantics.
- [ ] Reference semantics.
- [ ] Ownership transfer.
- [ ] Borrowing.
- [ ] Non-owning views (`span`, `string_view`).
- [ ] Raw pointer as observer vs owner convention — make it explicit.
- [ ] `unique_ptr` ownership transfer.
- [ ] Shared ownership only when genuinely shared.
- [ ] `const` correctness.
- [ ] Strong types vs primitive obsession.
- [ ] Enumerations.
- [ ] Vocabulary types: optional/variant/expected.
- [ ] Exceptions vs expected/error codes by boundary and domain.
- [ ] Rule of Zero.
- [ ] Immutability where useful.
- [ ] PImpl and ABI.
- [ ] Runtime polymorphism vs templates vs variant vs type erasure.
- [ ] Header hygiene.
- [ ] Minimal dependencies.
- [ ] Stable public interfaces.

---

# 13. Required implementations — educational, not production replacements

Do these without copying library implementations.

1. **Tracked object**
   - construction/copy/move/assignment/destruction counters.

2. **RAII resource wrapper**
   - file descriptor or file handle.

3. **Educational `UniquePtr<T>`**
   - move construction/assignment, reset/release/get, custom deleter basics.

4. **Educational reference-counted pointer**
   - enough to understand control blocks; explicitly document missing production concerns.

5. **Educational `Vector<T>`**
   - raw allocation, placement construction, destruction, growth, move/copy fallback, exception safety.

6. **Small type-erased callable wrapper**
   - enough to understand `std::function`-style erasure; small-buffer optimization is optional later.

7. **Variant-based state machine**
   - compare with virtual-polymorphic design.

8. **Template/concepts mini-library**
   - traits, variadics, constraints, tests.

9. **PImpl shared library**
   - demonstrate binary-boundary effects.

10. **C++20 coroutine tracer**
    - log frame/suspend/resume/destruction behavior.

11. **PMR experiment**
    - default allocator vs monotonic resource for a controlled workload.

12. **Bug zoo**
    - lifetime, UB, iterator invalidation, proxy, dangling view, ownership and exception bugs.

---

# 14. Required closed-book interview banks

Build these over time; do not wait until the end.

## 14.1 Core language — minimum 100 questions

Must include:
- initialization,
- conversions,
- overload resolution,
- const/reference rules,
- lifetime,
- object model,
- inheritance/virtual dispatch,
- exceptions,
- UB.

## 14.2 Scott Meyers — minimum 3 questions per item

42 items × 3 = **126 minimum questions**:

- one “state the rule” question,
- one code-prediction question,
- one design/trade-off question.

For difficult items (1–4, 14, 17–22, 23–30, 35–40), create more than three.

## 14.3 Templates — minimum 75 questions

Include:
- deduction,
- dependent names,
- specialization,
- two-phase lookup,
- variadics,
- SFINAE,
- traits,
- concepts,
- CRTP,
- overload-resolution interactions.

## 14.4 STL — minimum 100 questions

Include:
- container choice,
- complexity,
- invalidation,
- allocator behavior,
- algorithm preconditions,
- comparator/hash contracts,
- string_view lifetime,
- optional/variant/expected.

## 14.5 Toolchain/ABI/debugging — minimum 50 questions

Include:
- compile vs link failures,
- ODR,
- symbol visibility,
- vtables/ABI,
- shared libraries,
- sanitizers,
- debugging strategy.

## 14.6 Modern standards — minimum 100 questions

Split across:
- C++17,
- C++20,
- C++23,
- feature-selection/trade-offs.

---

# 15. CppValley extraction rule

**Never merge concepts only to satisfy a schedule.**

For each mastery unit, possible video types are:

1. Mental-model video.
2. “What the compiler actually does” experiment.
3. Broken-code/debugging video.
4. Build-it-from-scratch implementation.
5. Benchmark/performance investigation.
6. Edge-case/interview-trap compilation.
7. Code-review/refactor video.
8. Mock-interview video.
9. Standard-version comparison.
10. Architecture/API trade-off video.

One Scott item may generate one video or ten. That is expected.

Every serious CppValley video should end with **Interview Mode**:

- What is the simplest correct explanation?
- What changes for `const`?
- What changes for lvalue/rvalue?
- What are the lifetime/ownership implications?
- What are the exception implications?
- What are the performance implications?
- What is the common misconception?
- What alternative design would you consider?

---

# 16. Final Curriculum 01 exit examination

Do **not** mark C++ mastery complete because the reading list is finished.

The final gate is multi-part.

## Gate A — Code prediction

100 mixed snippets across:
- initialization,
- overload resolution,
- deduction,
- lifetime,
- move/forwarding,
- templates,
- STL,
- modern-standard features.

Target: **>=90%**, with explanation, not guessing.

## Gate B — Implementation

Closed-book:
- RAII wrapper,
- move-only type,
- forwarding wrapper,
- simplified vector core,
- one constrained generic API.

## Gate C — Debugging

Diagnose at least:
- dangling reference,
- UAF,
- iterator invalidation,
- ODR/link error,
- incorrect virtual override,
- exception-safety failure,
- forwarding-reference overload bug,
- string_view lifetime bug,
- UB exposed by optimization.

## Gate D — Design review

Given an API, discuss:
- ownership,
- lifetime,
- constness,
- error model,
- copying/moving,
- exception guarantee,
- ABI impact,
- template vs virtual vs type-erased design,
- standard-library vocabulary types.

## Gate E — Staff-level C++ interview

90–120 minutes, no notes:

1. 20 min core language/lifetime.
2. 20 min templates/modern C++.
3. 20 min STL/API trade-offs.
4. 20 min debugging/toolchain/ABI.
5. 20–40 min code/design problem.

Pass only when answers are precise, examples are correct, and uncertainty is explicitly bounded.

---

# 17. What comes after Curriculum 01

Once this exit gate is consistently passed, continue DreamRun in dependency order:

1. Concurrency and C++ memory model — Anthony Williams.
2. CPU/memory/performance — Fedor Pikus + profiling.
3. Linux systems and networking.
4. Low-latency/HFT engineering.
5. C++ architecture and Staff design — Klaus Iglberger.
6. Distributed systems + system design.
7. CUDA/GPU.
8. AI fundamentals and inference systems.
9. Full company-specific interview conversion.

DSA remains a parallel spaced-repetition track throughout.

---

# 18. Final completeness rule

This curriculum is a **living canonical checklist**, not an archive.

When a missing C++ topic is discovered:

- add it here in the correct dependency location,
- add a mastery gate/lab if needed,
- do **not** create competing `v2`, `old`, or `extra-cpp-plan` files,
- do not reduce existing depth to keep the document short.

The target is not to say “I finished Scott Meyers.” The target is to be able to reason about unfamiliar C++ code, write robust modern C++, debug difficult failures, discuss trade-offs, and survive deep follow-up questions from a strong C++ interviewer.