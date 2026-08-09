# Curriculum 01 — Modern C++ Mastery

This is the **only canonical C++ curriculum for DreamRun**.

It is intentionally linear. Follow **Unit 001 → Unit 002 → ...**. Do not jump ahead because a later topic looks exciting. Do not mark a unit complete because you read it once.

There is **no fixed video quota**. Each unit contains suggested CppValley videos; split a topic into more videos whenever the experiments justify it.

## How every unit works

For every unit, do these in order:

1. **Read exactly what is listed.**
2. **Close the source and explain it from memory.**
3. **Implement / experiment.**
4. **Break it deliberately.**
5. **Inspect with compiler/debugger/sanitizer/assembly when relevant.**
6. **Answer the mastery check without notes.**
7. **Only then record the suggested CppValley videos.**

The target of Curriculum 01 is not “finish Scott Meyers.” The target is: **C++ deep-dive questions should be one of your strongest interview areas.** Company loops still require DSA, concurrency, OS, networking, performance, architecture, system design, behavioral/leadership and—depending on role—CUDA/AI systems. Those are later DreamRun curricula.

---

# Stage 0 — C++ foundations Scott assumes

## Unit 001 — Translation units, declarations, definitions, ODR

**Read**
- cppreference: Definitions and ODR — https://en.cppreference.com/w/cpp/language/definition
- cppreference: Translation phases — https://en.cppreference.com/w/cpp/language/translation_phases
- C++ Core Guidelines: SF / source files sections.

**Do**
- Build a 3-translation-unit program.
- Create one undefined-reference error and one multiple-definition error.
- Compare declaration vs definition, ODR-use, inline function and inline variable.

**Videos**
- `From .cpp to Program: Translation Units and the ODR`
- `I Broke the One Definition Rule on Purpose`

**Mastery check**
Explain declaration, definition, ODR, ODR-use, translation unit and why `inline` is primarily an ODR/linkage concept rather than an optimization promise.

## Unit 002 — Linkage, namespaces, lookup and ADL

**Read**
- cppreference: Storage duration / linkage — https://en.cppreference.com/w/cpp/language/storage_duration
- Name lookup — https://en.cppreference.com/w/cpp/language/lookup
- ADL — https://en.cppreference.com/w/cpp/language/adl

**Do**
- Demonstrate internal/external/no linkage.
- Build a hidden-friend operator found by ADL.
- Create name-hiding and ambiguous lookup examples.

**Videos**
- `C++ Name Lookup: Why the Compiler Found THAT Function`
- `ADL and Hidden Friends: The Rule Behind operator<< Magic`

**Mastery check**
Predict lookup for qualified/unqualified names and explain when ADL participates.

## Unit 003 — Fundamental types, signedness, promotions and conversions

**Read**
- Fundamental types — https://en.cppreference.com/w/cpp/language/types
- Implicit conversions — https://en.cppreference.com/w/cpp/language/implicit_conversion
- Usual arithmetic conversions — https://en.cppreference.com/w/cpp/language/usual_arithmetic_conversions

**Do**
- Build 30 signed/unsigned/promotion cases.
- Compile with `-Wconversion -Wsign-conversion` where supported.
- Test narrowing and overflow behavior; distinguish defined, implementation-defined and undefined behavior.

**Videos**
- `Signed vs Unsigned: The C++ Bug That Passes Code Review`
- `Integer Promotions: Why Your char Became an int`

**Mastery check**
Predict types/results of mixed arithmetic without running the code.

## Unit 004 — Literals, object representation, size, alignment and padding

**Read**
- Literals — https://en.cppreference.com/w/cpp/language/expressions#Literals
- Object representation — https://en.cppreference.com/w/cpp/language/objects
- `sizeof` — https://en.cppreference.com/w/cpp/language/sizeof
- `alignof` — https://en.cppreference.com/w/cpp/language/alignof

**Do**
- Measure layouts of 20 structs.
- Reorder members and explain padding changes.
- Inspect addresses/alignment; use `std::bit_cast` later only where legal.

**Videos**
- `Why This 9-Byte Struct Takes 16 Bytes`
- `C++ Object Layout: Alignment and Padding Visualized`

**Mastery check**
Explain value representation vs object representation, padding, alignment and why layout is not fully portable.

## Unit 005 — Every major initialization form

**Read**
- Initialization — https://en.cppreference.com/w/cpp/language/initialization
- List initialization — https://en.cppreference.com/w/cpp/language/list_initialization
- Value initialization — https://en.cppreference.com/w/cpp/language/value_initialization
- Aggregate initialization — https://en.cppreference.com/w/cpp/language/aggregate_initialization

**Do**
- Create an `InitTracer` class.
- Test default-, value-, direct-, copy-, direct-list-, copy-list-, aggregate- and reference-initialization.
- Include most-vexing-parse and `initializer_list` overload cases.

**Videos**
- `C++ Has Too Many Initialization Forms — Here Is the Mental Model`
- `() vs {} vs ={}: I Tested Every Constructor Path`

**Mastery check**
Given unfamiliar declarations, state exactly which initialization form occurs and which constructor wins.

## Unit 006 — Pointers, references, cv-qualification and null

**Read**
- Pointers — https://en.cppreference.com/w/cpp/language/pointer
- References — https://en.cppreference.com/w/cpp/language/reference
- cv qualifiers — https://en.cppreference.com/w/cpp/language/cv
- `nullptr` — https://en.cppreference.com/w/cpp/language/nullptr

**Do**
- Solve 40 declaration-reading exercises.
- Compare `const T*`, `T* const`, `const T* const`, `T&`, `const T&`, `T&&`.
- Test null overloads with `0`, `NULL`, `nullptr`.

**Videos**
- `Pointers and const: Read Any C++ Declaration Correctly`
- `nullptr vs NULL vs 0: Overload Resolution Proves the Difference`

**Mastery check**
State mutability, reseatability, ownership implication and lifetime risk for each declaration.

## Unit 007 — Arrays, functions and decay

**Read**
- Arrays — https://en.cppreference.com/w/cpp/language/array
- Array-to-pointer conversion in implicit conversions.
- Function pointers — https://en.cppreference.com/w/cpp/language/pointer#Pointers_to_functions

**Do**
- Pass arrays/functions by value-like parameter, reference and template reference.
- Measure `sizeof` before/after decay.
- Preserve array extent with templates.

**Videos**
- `Your C++ Array Disappeared Into a Pointer`
- `How Templates Preserve Array Size Without std::array`

**Mastery check**
Predict when array/function type is preserved and when it decays.

## Unit 008 — Expressions, value categories and materialization

**Read**
- Value categories — https://en.cppreference.com/w/cpp/language/value_category
- Expressions — https://en.cppreference.com/w/cpp/language/expressions

**Do**
- Classify 50 expressions as lvalue/xvalue/prvalue.
- Use `decltype((expr))` to verify.
- Test temporary materialization and reference binding.

**Videos**
- `lvalue, xvalue, prvalue: Stop Memorizing and See the Model`
- `I Classified 50 C++ Expressions by Value Category`

**Mastery check**
Classify expressions without relying on “has a name” shortcuts.

## Unit 009 — Sequencing and evaluation order

**Read**
- Evaluation order — https://en.cppreference.com/w/cpp/language/eval_order

**Do**
- Build historical/unsequenced examples.
- Compare guaranteed order introduced in newer standards where applicable.
- Separate sequencing from CPU execution order.

**Videos**
- `C++ Evaluation Order: What Is Actually Guaranteed?`
- `Undefined Behavior From One Innocent-Looking Expression`

**Mastery check**
Explain sequenced-before, indeterminately sequenced and unsequenced at practical interview depth.

## Unit 010 — Functions, overload resolution and conversions

**Read**
- Overload resolution — https://en.cppreference.com/w/cpp/language/overload_resolution
- Converting constructor — https://en.cppreference.com/w/cpp/language/converting_constructor
- Conversion functions — https://en.cppreference.com/w/cpp/language/cast_operator

**Do**
- Create ambiguous overload sets.
- Mix exact matches, promotions, conversions, user-defined conversions and templates.
- Add deleted overloads and `explicit` constructors.

**Videos**
- `C++ Overload Resolution: How the Compiler Chooses a Function`
- `I Built an Overload Set Designed to Confuse Senior Engineers`

**Mastery check**
List viable candidates and rank the winning conversion sequence for mixed cases.

## Unit 011 — Classes, constructors, destructors and member initialization

**Read**
- Classes — https://en.cppreference.com/w/cpp/language/classes
- Constructors — https://en.cppreference.com/w/cpp/language/constructor
- Destructors — https://en.cppreference.com/w/cpp/language/destructor

**Do**
- Trace base/member construction and destruction order.
- Demonstrate initializer-list textual order not controlling member construction order.
- Test delegating/converting/explicit constructors.

**Videos**
- `C++ Construction Order: The Initializer List Can Lie to You`
- `Constructors, Destructors and Object Birth/Death Traced`

**Mastery check**
Predict exact construction/destruction order in inheritance + composition cases.

## Unit 012 — Special member functions and Rule of Zero/Three/Five

**Read**
- Rule of three/five/zero — https://en.cppreference.com/w/cpp/language/rule_of_three
- Copy constructor / move constructor / assignments on cppreference.

**Do**
- Build a trait matrix of classes with user-declared destructor/copy/move operations.
- Use `is_copy_constructible`, `is_move_constructible`, etc.

**Videos**
- `Rule of Zero, Three and Five: What the Compiler Generates`
- `I Changed One Destructor and Lost My Move Constructor`

**Mastery check**
Predict which special members are declared, deleted or suppressed.

## Unit 013 — Inheritance, virtual dispatch, RTTI and slicing

**Read**
- Derived classes — https://en.cppreference.com/w/cpp/language/derived_class
- Virtual functions — https://en.cppreference.com/w/cpp/language/virtual
- `dynamic_cast` — https://en.cppreference.com/w/cpp/language/dynamic_cast
- `typeid` — https://en.cppreference.com/w/cpp/language/typeid

**Do**
- Build polymorphic hierarchy with/without virtual destructor.
- Demonstrate slicing.
- Inspect ABI-specific vtable/vptr behavior in Compiler Explorer/gdb and label it implementation-specific.

**Videos**
- `Virtual Functions: What C++ Guarantees vs What the ABI Does`
- `Object Slicing: The Polymorphism Bug That Compiles`

**Mastery check**
Explain virtual dispatch during construction/destruction, slicing, RTTI and destructor requirements.

## Unit 014 — Storage duration, object lifetime and temporary lifetime extension

**Read**
- Storage duration — https://en.cppreference.com/w/cpp/language/storage_duration
- Object lifetime — https://en.cppreference.com/w/cpp/language/lifetime

**Do**
- Build lifetime-extension examples and non-extension counterexamples.
- Create use-after-scope/dangling-reference bug zoo and run ASan.

**Videos**
- `C++ Object Lifetime: The Rule Behind Thousands of Bugs`
- `Temporary Lifetime Extension: 10 Cases, 4 Traps`

**Mastery check**
For any object/reference in sample code, state lifetime begin/end and whether the reference can dangle.

## Unit 015 — Dynamic memory, operator new/delete and placement new

**Read**
- `new` expression — https://en.cppreference.com/w/cpp/language/new
- `delete` expression — https://en.cppreference.com/w/cpp/language/delete
- Memory allocation functions — https://en.cppreference.com/w/cpp/memory/new/operator_new

**Do**
- Separate allocation from construction.
- Implement placement-new experiment into aligned raw storage.
- Deliberately mismatch delete forms and detect errors with sanitizers.

**Videos**
- `new Is Not operator new: Allocation vs Construction`
- `Placement New: Constructing Objects in Raw Memory`

**Mastery check**
Explain allocation function vs new-expression and deallocation vs destructor.

## Unit 016 — Exceptions and exception-safety guarantees

**Read**
- Exceptions — https://en.cppreference.com/w/cpp/language/exceptions
- `noexcept` specification — https://en.cppreference.com/w/cpp/language/noexcept_spec
- C++ Core Guidelines error handling section.

**Do**
- Build a class that leaks/corrupts state on exception, then make it basic/strong/no-throw safe.
- Trace stack unwinding.

**Videos**
- `Exception Safety: Basic vs Strong vs No-Throw`
- `I Injected Exceptions Into a C++ Class Until It Broke`

**Mastery check**
Given an operation, state its guarantee and how RAII makes it possible.

## Unit 017 — Casts and type conversions

**Read**
- `static_cast` — https://en.cppreference.com/w/cpp/language/static_cast
- `dynamic_cast` — https://en.cppreference.com/w/cpp/language/dynamic_cast
- `const_cast` — https://en.cppreference.com/w/cpp/language/const_cast
- `reinterpret_cast` — https://en.cppreference.com/w/cpp/language/reinterpret_cast

**Do**
- Build safe/unsafe examples for every cast.
- Demonstrate why C-style cast hides intent.

**Videos**
- `The Four C++ Casts: What Each One Actually Promises`
- `reinterpret_cast: What It Does NOT Make Safe`

**Mastery check**
Choose the correct cast—or refuse to cast—for unfamiliar scenarios.

## Unit 018 — Undefined behavior, implementation-defined and unspecified behavior

**Read**
- UB overview — https://en.cppreference.com/w/cpp/language/ub

**Do**
- Create signed overflow, out-of-bounds, dangling, invalid shift and strict lifetime examples.
- Observe optimizer effects under `-O0` vs `-O2/-O3`.

**Videos**
- `Undefined Behavior: Why the Optimizer Is Allowed to Betray You`
- `I Compiled the Same UB at -O0 and -O3`

**Mastery check**
Distinguish undefined, unspecified and implementation-defined behavior with examples.

---

# Stage 1 — Scott Meyers, Effective Modern C++, every item in order

> **Primary reading for Units 019–060:** Scott Meyers, *Effective Modern C++*, the exact item named below. Read the entire item, including sidebars/notes. Then read the linked cppreference pages and run the lab.

## Unit 019 — Scott Item 1: Understand template type deduction

**Read**
- Scott Item 1 completely.
- Template argument deduction — https://en.cppreference.com/w/cpp/language/template_argument_deduction

**Do**
- 100-case deduction matrix: `T`, `T&`, `const T&`, `T&&`, pointers, arrays, functions, cv/ref combinations.

**Videos**
- `Template Type Deduction: The Complete Mental Model`
- `I Tested 100 Template-Deduction Cases Against GCC and Clang`
- `Arrays, Functions and cv-ref Traps in Template Deduction`

**Mastery check**
≥90% closed-book on the 100-case matrix.

## Unit 020 — Scott Item 2: Understand auto type deduction

**Read**
- Scott Item 2.
- Placeholder type deduction — https://en.cppreference.com/w/cpp/language/auto

**Do**
- Rewrite Unit 019 cases with `auto`, `auto&`, `const auto&`, `auto&&` and braced initialization.

**Videos**
- `auto Is Template Deduction—Except When It Isn't`
- `Brace Initialization vs auto: The Special Rule`

**Mastery check**
Predict both deduced type and expression category in mixed cases.

## Unit 021 — Scott Item 3: Understand decltype

**Read**
- Scott Item 3.
- `decltype` — https://en.cppreference.com/w/cpp/language/decltype

**Do**
- 40-case matrix covering names, member access, lvalues/xvalues/prvalues, parentheses and `decltype(auto)`.

**Videos**
- `decltype(x) vs decltype((x)): Two Parentheses Change the Type`
- `decltype(auto): Power Tool or Dangling-Reference Machine?`

**Mastery check**
Predict every case without compiler help.

## Unit 022 — Scott Item 4: Know how to view deduced types

**Read**
- Scott Item 4.
- `type_traits` overview — https://en.cppreference.com/w/cpp/header/type_traits

**Do**
- Inspect types via compiler error, `static_assert`, IDE/debugger and runtime naming; document information each method loses.

**Videos**
- `Four Ways to Ask C++ “What Type Is This?”`
- `Why typeid().name() Can Lie by Omission`

**Mastery check**
Choose a reliable type-inspection method for compile-time deduction problems.

## Unit 023 — Scott Item 5: Prefer auto to explicit type declarations

**Read**
- Scott Item 5.

**Do**
- Iterator, lambda closure and `unordered_map` key/value iteration examples; find accidental copies from wrong explicit types.

**Videos**
- `auto Prevented a Hidden Copy in My unordered_map Loop`
- `When auto Makes C++ Safer—and When It Hides Intent`

**Mastery check**
Explain correctness/maintenance reasons, not just typing convenience.

## Unit 024 — Scott Item 6: Explicitly typed initializer idiom

**Read**
- Scott Item 6.
- `vector<bool>` notes — https://en.cppreference.com/w/cpp/container/vector_bool

**Do**
- Build an educational proxy type; show `auto` preserving proxy and explicit materialization fixing lifetime/conversion behavior.

**Videos**
- `vector<bool> Is Not a vector of bools`
- `When auto Captures a Proxy Instead of a Value`

**Mastery check**
Recognize proxy/expression-template hazards from an API signature.

## Unit 025 — Scott Item 7: Distinguish () and {} when creating objects

**Read**
- Scott Item 7.
- List initialization — https://en.cppreference.com/w/cpp/language/list_initialization

**Do**
- Exhaustive overload matrix with normal constructors and `initializer_list`; include vector size/value trap and narrowing.

**Videos**
- `() vs {}: The C++ Initialization War`
- `initializer_list Wins Overloads You Didn't Expect`

**Mastery check**
Predict constructor selection for all matrix cases.

## Unit 026 — Scott Item 8: Prefer nullptr to 0 and NULL

**Read**
- Scott Item 8.
- `nullptr` page.

**Do**
- Pointer/integer overload sets and template forwarding cases.

**Videos**
- `nullptr vs NULL vs 0: Compiler Proof`
- `Why NULL Breaks Generic C++ APIs`

**Mastery check**
Explain `std::nullptr_t` and overload behavior.

## Unit 027 — Scott Item 9: Prefer alias declarations to typedefs

**Read**
- Scott Item 9.
- Type aliases — https://en.cppreference.com/w/cpp/language/type_alias

**Do**
- Convert nested typedef-heavy traits to aliases and alias templates.

**Videos**
- `using vs typedef: The Difference Matters in Templates`
- `Alias Templates Remove an Entire Layer of Metaprogramming`

**Mastery check**
Write alias templates from memory and explain dependent-type advantages.

## Unit 028 — Scott Item 10: Prefer scoped enums

**Read**
- Scott Item 10.
- Enumeration declarations — https://en.cppreference.com/w/cpp/language/enum

**Do**
- Compare unscoped/scoped enum name pollution and conversions; choose explicit underlying types for wire/storage examples.

**Videos**
- `enum vs enum class: More Than Namespace Pollution`
- `Enum Underlying Types and Serialization Traps`

**Mastery check**
Explain scope, conversion, forward declaration and ABI/storage implications.

## Unit 029 — Scott Item 11: Prefer deleted functions

**Read**
- Scott Item 11.
- Function definition `= delete` — https://en.cppreference.com/w/cpp/language/function#Deleted_functions

**Do**
- Delete copy operations and dangerous conversions; compare with private undeclared functions.

**Videos**
- `= delete: Turning Bad Calls Into Good Compiler Errors`
- `Deleted Functions Still Participate in Overload Resolution`

**Mastery check**
Predict how deleted candidates affect overload resolution.

## Unit 030 — Scott Item 12: Declare overriding functions override

**Read**
- Scott Item 12.
- Virtual functions page.

**Do**
- Break overrides with `const`, ref qualifiers and parameter changes; let `override` catch every case.

**Videos**
- `override Finds Bugs Humans Miss`
- `One const Broke My Virtual Override`

**Mastery check**
Explain override matching and `final`.

## Unit 031 — Scott Item 13: Prefer const_iterators

**Read**
- Scott Item 13.
- Iterator library — https://en.cppreference.com/w/cpp/iterator

**Do**
- Search/insert/erase workflows using `cbegin/cend` and const iterators.

**Videos**
- `iterator vs const_iterator: Mutability Is API Design`
- `Modern C++ const Iterators Without Legacy Pain`

**Mastery check**
Choose iterator constness based on operation intent.

## Unit 032 — Scott Item 14: Declare functions noexcept if they will not emit exceptions

**Read**
- Scott Item 14.
- `noexcept` specification page.

**Do**
- Vector relocation with throwing vs `noexcept` move; inspect `is_nothrow_move_constructible`.

**Videos**
- `One noexcept Changed How vector Reallocated`
- `noexcept Is a Contract, Not a Performance Keyword`

**Mastery check**
Explain termination, conditional noexcept and container consequences.

## Unit 033 — Scott Item 15: Use constexpr whenever possible

**Read**
- Scott Item 15.
- Constant expressions — https://en.cppreference.com/w/cpp/language/constant_expression
- `constexpr` — https://en.cppreference.com/w/cpp/language/constexpr

**Do**
- Build compile-time validated utility; compare what C++14/17/20 allow.

**Videos**
- `constexpr Does Not Mean “Always Compile Time”`
- `Turning Runtime Bugs Into Compile-Time Errors With constexpr`

**Mastery check**
Explain constant evaluation vs constexpr eligibility.

## Unit 034 — Scott Item 16: Make const member functions thread safe

**Read**
- Scott Item 16.
- `mutable` — https://en.cppreference.com/w/cpp/keyword/mutable

**Do**
- Create lazy cache race; fix with mutex and with atomic only when invariant allows.

**Videos**
- `const Does NOT Mean Thread Safe`
- `mutable, Caches and the Hidden Data Race`

**Mastery check**
Explain logical constness and why multiple atomics may fail to preserve an invariant.

## Unit 035 — Scott Item 17: Understand special member generation

**Read**
- Scott Item 17.
- Rule of three/five/zero page.

**Do**
- Expand Unit 012 trait matrix to bases/members that suppress/delete operations.

**Videos**
- `Exactly When C++ Generates Copy and Move Operations`
- `The Special-Member Matrix Every C++ Interviewer Loves`

**Mastery check**
Predict declaration/deletion for complex classes.

## Unit 036 — Scott Item 18: Use unique_ptr for exclusive ownership

**Read**
- Scott Item 18.
- `unique_ptr` — https://en.cppreference.com/w/cpp/memory/unique_ptr

**Do**
- Implement educational `UniquePtr<T>` with move/reset/release/get/custom deleter basics.
- Test array and incomplete-type/PImpl cases.

**Videos**
- `unique_ptr Internals: Ownership Without Garbage Collection`
- `I Built unique_ptr From Scratch`
- `Custom Deleters Can Change unique_ptr's Size`

**Mastery check**
Design exclusive-ownership APIs without raw-owning pointers.

## Unit 037 — Scott Item 19: Use shared_ptr for shared ownership

**Read**
- Scott Item 19.
- `shared_ptr` — https://en.cppreference.com/w/cpp/memory/shared_ptr

**Do**
- Implement simplified control block/ref count.
- Explore custom deleter, aliasing constructor, `enable_shared_from_this` concept, thread-safety scope.

**Videos**
- `shared_ptr Control Block: What Actually Gets Allocated?`
- `I Built Reference Counting—and Found the Costs`
- `shared_ptr Thread Safety Is Easy to Misunderstand`

**Mastery check**
Separate object thread safety from control-block reference-count safety.

## Unit 038 — Scott Item 20: Use weak_ptr for potentially dangling shared observations

**Read**
- Scott Item 20.
- `weak_ptr` — https://en.cppreference.com/w/cpp/memory/weak_ptr

**Do**
- Build a shared_ptr cycle and break it; test expiration/lock.

**Videos**
- `The shared_ptr Cycle That Leaks Forever`
- `weak_ptr: Non-Owning Access Without a Dangling Raw Pointer`

**Mastery check**
Draw ownership graph and identify where weak ownership belongs.

## Unit 039 — Scott Item 21: Prefer make_unique/make_shared

**Read**
- Scott Item 21.
- `make_unique`, `make_shared` cppreference pages.

**Do**
- Instrument allocation count; show co-allocation and weak-retention trade-off.

**Videos**
- `make_shared Really Can Use One Allocation`
- `The make_shared Trade-Off Nobody Mentions`

**Mastery check**
State when factory helpers are preferable and when direct construction is justified.

## Unit 040 — Scott Item 22: PImpl with smart pointers

**Read**
- Scott Item 22.
- Incomplete types — https://en.cppreference.com/w/cpp/language/type#Incomplete_type

**Do**
- Build a small PImpl library; place destructor/move definitions out of line; change private layout without touching public header.

**Videos**
- `PImpl: How C++ Hides Implementation and Protects ABI`
- `Why unique_ptr to an Incomplete Type Can Fail at Destruction`

**Mastery check**
Explain compile-time dependency, complete-type requirement and ABI motivation.

## Unit 041 — Scott Item 23: Understand std::move and std::forward

**Read**
- Scott Item 23.
- `std::move` — https://en.cppreference.com/w/cpp/utility/move
- `std::forward` — https://en.cppreference.com/w/cpp/utility/forward

**Do**
- Instrument copies/moves; test moving from const; prove utilities are casts.

**Videos**
- `std::move Does NOT Move Anything`
- `Why std::move(const T) Usually Copies`

**Mastery check**
Explain exactly what each utility returns and when an actual move operation occurs.

## Unit 042 — Scott Item 24: Distinguish forwarding references from rvalue references

**Read**
- Scott Item 24.
- Reference page + template deduction page.

**Do**
- Build matrix of `T&&`, `const T&&`, class-template `T&&`, `auto&&`, generic lambda `auto&&`.

**Videos**
- `T&& Is Not Always an Rvalue Reference`
- `Forwarding References: The Exact Rule`

**Mastery check**
Identify forwarding references purely from declaration context.

## Unit 043 — Scott Item 25: Use move on rvalue refs, forward on forwarding refs

**Read**
- Scott Item 25.

**Do**
- Named rvalue-reference experiments; last-use/multiple-forward cases; show explicit move harming NRVO.

**Videos**
- `Named Rvalue References Are Lvalues`
- `The std::move That Disabled Copy Elision`

**Mastery check**
Place move/forward correctly in a wrapper and justify every use.

## Unit 044 — Scott Item 26: Avoid overloading on forwarding references

**Read**
- Scott Item 26.

**Do**
- Reproduce greedy overload, forwarding constructor hijacking and derived/base surprises.

**Videos**
- `The Perfect-Forwarding Constructor That Hijacked Copy Construction`
- `Why T&& Overloads Are Too Greedy`

**Mastery check**
Spot forwarding-overload hazards in code review.

## Unit 045 — Scott Item 27: Alternatives to forwarding-reference overloads

**Read**
- Scott Item 27.
- `enable_if` — https://en.cppreference.com/w/cpp/types/enable_if
- Concepts later in Unit 103+.

**Do**
- Implement same API using separate names, const-ref, by-value, tag dispatch and constraints.

**Videos**
- `Five Alternatives to a Dangerous T&& Overload`
- `Tag Dispatch to Concepts: Constraining Generic APIs`

**Mastery check**
Choose an alternative based on API semantics, not cleverness.

## Unit 046 — Scott Item 28: Understand reference collapsing

**Read**
- Scott Item 28.
- Reference collapsing section on reference page.

**Do**
- Build all collapse combinations via aliases, deduction and decltype.

**Videos**
- `Reference Collapsing in One Table—and Why It Exists`
- `How Reference Collapsing Makes Perfect Forwarding Possible`

**Mastery check**
Derive all cases without memorized code snippets.

## Unit 047 — Scott Item 29: Assume move may not exist, be cheap, or be used

**Read**
- Scott Item 29.

**Do**
- Benchmark small/trivial, SSO string, vector, array, const objects and throwing move types.

**Videos**
- `Move Semantics Is Not Automatically Faster`
- `I Benchmarked Copy vs Move Across Five C++ Types`

**Mastery check**
Explain why a specific “move” path may copy or offer little benefit.

## Unit 048 — Scott Item 30: Perfect-forwarding failure cases

**Read**
- Scott Item 30.

**Do**
- Reproduce braced initializer, null constant, overloaded function/template, bit-field and static-const historical cases.

**Videos**
- `Perfect Forwarding Is Not Perfect: Every Major Failure Case`
- `Why You Can't Perfect-Forward a Bit-Field`

**Mastery check**
Diagnose the failure and propose the cleanest workaround.

## Unit 049 — Scott Item 31: Avoid default lambda capture modes

**Read**
- Scott Item 31.
- Lambda expressions — https://en.cppreference.com/w/cpp/language/lambda

**Do**
- Create dangling `this` and stale-capture examples; compare explicit capture.

**Videos**
- `[=] and [&] Can Hide Lifetime Bugs`
- `The Lambda That Outlived this`

**Mastery check**
Audit closure ownership/lifetime from a capture list.

## Unit 050 — Scott Item 32: Use init capture to move objects into closures

**Read**
- Scott Item 32.
- Lambda capture section.

**Do**
- Capture move-only resource/state; compare ownership before/after capture.

**Videos**
- `Moving Ownership Into a Lambda`
- `Init Capture: Lambdas Can Own More Than Copies`

**Mastery check**
Design callback ownership explicitly.

## Unit 051 — Scott Item 33: Forward auto&& lambda parameters with decltype

**Read**
- Scott Item 33.

**Do**
- Generic forwarding lambda with lvalue/rvalue tests and static assertions.

**Videos**
- `Perfect Forwarding Inside Generic Lambdas`
- `Why decltype(param) Is the Right Type for std::forward Here`

**Mastery check**
Write the pattern from memory and explain why it works.

## Unit 052 — Scott Item 34: Prefer lambdas to std::bind

**Read**
- Scott Item 34.
- `std::bind` — https://en.cppreference.com/w/cpp/utility/functional/bind

**Do**
- Implement same callback with bind and lambda; test overload resolution, captures, evaluation and generated code.

**Videos**
- `std::bind vs Lambda: Why Modern C++ Chose Lambdas`
- `I Replaced a bind Expression and the Types Became Obvious`

**Mastery check**
Explain remaining niche use cases without recommending bind by default.

## Unit 053 — Scott Item 35: Prefer task-based to thread-based programming

**Read**
- Scott Item 35.
- Futures — https://en.cppreference.com/w/cpp/thread/future

**Do**
- Compare explicit thread result/exception handling with async/future.

**Videos**
- `Thread vs Task: What Abstraction Do You Actually Need?`
- `Returning Values and Exceptions From Asynchronous Work`

**Mastery check**
State when explicit thread identity/control is genuinely required.

## Unit 054 — Scott Item 36: Specify launch::async when asynchronicity is essential

**Read**
- Scott Item 36.
- `std::async` — https://en.cppreference.com/w/cpp/thread/async

**Do**
- Demonstrate deferred vs async behavior and `wait_for` status.

**Videos**
- `std::async May Not Be Asynchronous`
- `launch::deferred vs launch::async: Run It and See`

**Mastery check**
Explain default policy uncertainty and correctness implications.

## Unit 055 — Scott Item 37: Make std::threads unjoinable on all paths

**Read**
- Scott Item 37.
- `std::thread` — https://en.cppreference.com/w/cpp/thread/thread

**Do**
- Trigger termination from joinable thread destructor; build RAII wrapper; compare later with jthread.

**Videos**
- `Destroying a Joinable std::thread Calls terminate`
- `RAII for Threads: Making Every Exit Path Safe`

**Mastery check**
Handle exceptions/early returns without leaking thread lifecycle.

## Unit 056 — Scott Item 38: Varying thread-handle destructor behavior

**Read**
- Scott Item 38.
- Re-read `std::async` and future destructor notes.

**Do**
- Compare destructor behavior of thread and futures from different sources.

**Videos**
- `Why std::thread and std::future Destructors Behave Differently`
- `The Future Destructor That Can Wait`

**Mastery check**
Never assume a generic “async handle” destruction policy.

## Unit 057 — Scott Item 39: void futures for one-shot event communication

**Read**
- Scott Item 39.
- `promise`, `future`, `shared_future` cppreference pages.

**Do**
- Implement one-shot signal with promise/future and condition variable; compare semantics.

**Videos**
- `One-Shot Thread Signaling With promise<void>`
- `Condition Variable vs Future: Same Goal, Different Semantics`

**Mastery check**
Choose primitive based on one-shot/repeated state and ownership.

## Unit 058 — Scott Item 40: atomic for concurrency, volatile for special memory

**Read**
- Scott Item 40.
- `volatile` — https://en.cppreference.com/w/cpp/language/cv
- `std::atomic` — https://en.cppreference.com/w/cpp/atomic/atomic

**Do**
- Data race with volatile counter; compare atomic. Do not yet deep-dive memory ordering—that is Curriculum 02.

**Videos**
- `volatile Is NOT a Thread-Safety Keyword`
- `Atomic vs volatile: Two Completely Different Problems`

**Mastery check**
Explain exactly what volatile does not provide.

## Unit 059 — Scott Item 41: Consider pass by value for cheap-to-move, always-copied parameters

**Read**
- Scott Item 41.

**Do**
- Compare const-ref + copy, overload pair, and by-value + move for lvalue/rvalue callers; count operations.

**Videos**
- `Pass by Value vs const& vs T&&: Count the Operations`
- `When “Take by Value and Move” Is Actually Good API Design`

**Mastery check**
State conditions under which the technique is beneficial and when it is not.

## Unit 060 — Scott Item 42: Consider emplacement instead of insertion

**Read**
- Scott Item 42.
- Vector `emplace_back` / `push_back` cppreference pages.

**Do**
- Count constructions; test explicit constructors and resource ownership hazards.

**Videos**
- `emplace_back Is Not Always Faster Than push_back`
- `The Explicit Constructor emplace Can Call but push Cannot`

**Mastery check**
Choose emplacement based on construction semantics, not style folklore.

### Scott gate

Before Unit 061:
- Answer at least **3 interview questions for every Scott item**.
- Do a closed-book 90-minute review of Items 1–42.
- Any item that cannot be explained at senior depth is repeated.

---

# Stage 2 — Move semantics beyond Scott

> Primary source: Nicolai Josuttis, *C++ Move Semantics — The Complete Guide*. Read the named topic(s) from the book's table of contents in order.

## Unit 061 — Move motivation, rvalue refs, std::move, members

**Read**
- Josuttis topics: `Motivation of move semantics`, `Performance benefits`, `Rvalue references`, `std::move()`, `std::move() for members and member functions`.

**Do**
- Rebuild tracked-resource examples from scratch.

**Videos**
- `Move Semantics From Resource Ownership First Principles`
- `Moving Members Correctly in Real Classes`

**Gate**
Explain the resource-transfer model without using “rvalues are temporary” as the whole explanation.

## Unit 062 — Self-move, overload resolution, xvalues and decltype

**Read**
- Josuttis: `Self-move`, `Overload resolution with move semantics`, `Value categories and xvalues`, `decltype with expressions`.

**Do**
- Self-move-assignment torture tests; overload sets with copy/move/const&&.

**Videos**
- `Self Move Assignment: Must Your Type Survive x = std::move(x)?`
- `Move Overload Resolution Under the Microscope`

**Gate**
Reason about self-move safety and overload selection.

## Unit 063 — Rule of five/three, move-aware member initialization and ref qualifiers

**Read**
- Josuttis: `Rule of five or three`, `How to initialize members with move semantics`, `Overloading on reference qualifiers`, `The return type of getters`.

**Do**
- Design ref-qualified getters (`&`, `const&`, `&&`) and test lifetime consequences.

**Videos**
- `Ref-Qualified Member Functions: Different APIs for lvalues and rvalues`
- `Your Getter May Return a Dangling Reference From a Temporary`

**Gate**
Design getter return types for owned/view data safely.

## Unit 064 — Move in polymorphic hierarchies and const rvalues

**Read**
- Josuttis: `Move semantics in polymorphic class hierarchies`, `const rvalue references (const&&)`.

**Do**
- Base/derived move/copy matrix; show slicing and virtual-clone alternatives.

**Videos**
- `Move Semantics Meets Polymorphism`
- `const T&& Exists—But When Is It Useful?`

**Gate**
Explain why polymorphic/value semantics need deliberate design.

## Unit 065 — Generic move: forwarding, perfect passing, auto&&

**Read**
- Josuttis generic-code topics through `auto&&`.

**Do**
- Build forwarding wrapper, forwarding constructor, perfect-pass pipeline.

**Videos**
- `Perfect Passing: Value Category Across Multiple Layers`
- `auto&& Beyond Range-for: Universal Reference in Disguise`

**Gate**
Preserve caller category through two forwarding layers.

## Unit 066 — Perfect returning, decltype(auto), lambdas and range-for

**Read**
- Josuttis: `Perfect returning`, `decltype(auto)`, `Move semantics in lambdas`, `Move semantics in range-based for loops`.

**Do**
- Build wrapper returning references/values correctly; test moved elements in ranges.

**Videos**
- `Perfect Returning: When decltype(auto) Is the Right Tool`
- `Move Semantics in Range-Based for Loops`

**Gate**
Avoid dangling/performance mistakes in return forwarding.

## Unit 067 — Move-only standard-library types and move algorithms

**Read**
- Josuttis standard-library topics: move-only types, streams, threads, unique pointers, moving algorithms, move iterators.

**Do**
- Move streams/unique_ptrs through containers/algorithms; use move iterators deliberately.

**Videos**
- `Move Iterators: Turning Copies Into Moves`
- `Why Some Standard-Library Types Are Move-Only`

**Gate**
Explain semantic reason for move-only design.

## Unit 068 — Strings, containers, shared_ptr, pair and optional move behavior

**Read**
- Josuttis remaining standard-library move topics.

**Do**
- Instrument vector/array/string/shared_ptr/pair/optional moves and allocator-related caveats.

**Videos**
- `Moving a vector Is Cheap—Until Allocators Change the Rules`
- `What Does Moving shared_ptr Actually Cost?`

**Gate**
Never infer move cost solely from syntax.

---

# Stage 3 — Templates to interview/library-author depth

> Primary source: Vandevoorde/Josuttis/Gregor, *C++ Templates: The Complete Guide, 2nd Edition*.

## Unit 069 — Function templates

**Read**
- Templates 2e Chapter 1: sections 1.1–1.7.

**Do**
- Generic max-like functions, multiple parameters, defaults, overloads.

**Videos**
- `Function Templates From Definition to Overload Resolution`
- `Why Two Function Templates Become Ambiguous`

**Gate**
Explain deduction vs explicit template arguments and overload interaction.

## Unit 070 — Class templates, specialization, aliases and CTAD

**Read**
- Chapter 2: sections 2.1–2.11.

**Do**
- Build Stack<T>, full/partial specialization, alias and deduction guide.

**Videos**
- `Class Templates: Specialization, Partial Specialization and CTAD`
- `I Built a Deduction Guide the Compiler Couldn't Invent`

**Gate**
Know what can/cannot be partially specialized.

## Unit 071 — Non-type template parameters

**Read**
- Chapter 3.

**Do**
- Fixed-size buffer/policy examples using integral and `auto` NTTPs; later compare C++20 expanded NTTP support.

**Videos**
- `Non-Type Template Parameters: Values as Types' Compile-Time Partners`
- `auto as a Template Parameter`

**Gate**
Choose type vs non-type parameter correctly.

## Unit 072 — Variadic templates and fold expressions

**Read**
- Chapter 4.

**Do**
- Variadic logger, tuple-like processing, left/right fold experiments.

**Videos**
- `Variadic Templates Without Recursive Boilerplate`
- `Fold Expressions: Left Fold vs Right Fold Visualized`

**Gate**
Expand packs correctly and predict fold associativity.

## Unit 073 — Tricky template basics

**Read**
- Chapter 5, all sections: `typename`, zero initialization, `this->`, arrays/string literals, member templates, variable templates, template-template parameters.

**Do**
- Create one minimal failing/fixed case for every section.

**Videos**
- `Why Templates Need typename and this->`
- `Template-Template Parameters Without Fear`

**Gate**
Explain dependent names and two-phase lookup motivation at a practical level.

## Unit 074 — Perfect forwarding and enable_if

**Read**
- Chapter 6.

**Do**
- Special member function template hazards; enable/disable overloads with enable_if.

**Videos**
- `enable_if Before Concepts: How SFINAE Shaped Modern C++`
- `A Templated Constructor Can Break Your Copy Constructor`

**Gate**
Read legacy SFINAE code confidently.

## Unit 075 — By value or by reference in templates

**Read**
- Chapter 7.

**Do**
- Arrays/string literals, `std::ref`, return-value and recommended parameter declaration experiments.

**Videos**
- `Generic APIs: T, T&, const T&, T&&—Choose Deliberately`
- `std::ref and Why References Aren't Normal Values`

**Gate**
Design generic function parameter forms from semantics.

## Unit 076 — Compile-time programming, SFINAE and constexpr if

**Read**
- Chapter 8.

**Do**
- Trait selection, SFINAE detection and `if constexpr` equivalent.

**Videos**
- `SFINAE: Substitution Failure Is Not an Error, Finally Explained`
- `if constexpr Replaced Whole Families of Template Tricks`

**Gate**
Explain immediate-context failure and branch discard.

## Unit 077 — Templates in practice and terminology

**Read**
- Chapters 9 and 10.

**Do**
- Inclusion model, inline/templates, error decoding, substitution vs instantiation vs specialization.

**Videos**
- `Why Template Definitions Usually Live in Headers`
- `Substitution vs Instantiation vs Specialization`

**Gate**
Use terminology precisely in interview explanations.

## Unit 078 — Generic libraries and callable machinery

**Read**
- Chapter 11.

**Do**
- Generic callable wrapper using `std::invoke`; reference template parameter traps; deferred evaluation.

**Videos**
- `What Counts as Callable in Modern C++?`
- `std::invoke: One Interface for Functions, Members and Functors`

**Gate**
Write generic callable code that preserves semantics.

## Unit 079 — Template parameters, names and lookup in depth

**Read**
- Chapters 12 and 13.

**Do**
- Dependent/nondependent names, lookup timing, inheritance from dependent base.

**Videos**
- `Two-Phase Lookup: Why Template Errors Appear “Late”`
- `Dependent Base Classes and the this-> Mystery`

**Gate**
Predict whether lookup happens at definition or instantiation.

## Unit 080 — Instantiation model and explicit instantiation

**Read**
- Chapter 14.

**Do**
- On-demand/lazy instantiation and explicit-instantiation builds across translation units.

**Videos**
- `When Does a C++ Template Actually Get Instantiated?`
- `Explicit Instantiation to Control Build Times and Symbols`

**Gate**
Explain instantiation model and practical build impact.

## Unit 081 — Template deduction in depth

**Read**
- Chapter 15, sections 15.1–15.12.

**Do**
- Special deduction situations, initializer lists, packs, rvalue refs, SFINAE limitations, CTAD.

**Videos**
- `Template Deduction: The Deep Version Scott Couldn't Fit in One Item`
- `Non-Deduced Contexts: Why the Compiler Stops Guessing`

**Gate**
Solve advanced deduction cases beyond Scott Item 1.

## Unit 082 — Specialization and overloading in depth

**Read**
- Chapter 16.

**Do**
- Function overload vs explicit specialization; partial class/variable specialization.

**Videos**
- `Overload or Specialize? C++ Templates Have Different Rules`
- `Why Function Templates Cannot Be Partially Specialized`

**Gate**
Choose specialization/overload mechanism correctly.

## Unit 083 — Static polymorphism, traits, tag dispatch, CRTP and type erasure

**Read**
- Chapters 18–22, focusing on dynamic vs static polymorphism, traits/policies, tag dispatch, enabling/disabling, EBCO, CRTP, mixins, type erasure and performance considerations.

**Do**
- Implement the same Strategy interface via virtual functions, CRTP, `std::function`/type erasure and concepts later; benchmark carefully.

**Videos**
- `Virtual vs CRTP vs Type Erasure: Four Kinds of Polymorphism`
- `CRTP: Static Polymorphism Without Virtual Dispatch`
- `Type Erasure: How std::function Hides Concrete Types`

**Gate**
Choose a polymorphism model based on ABI, extensibility, compile time and runtime trade-offs.

## Unit 084 — Metaprogramming, typelists, tuples, variants and template debugging

**Read**
- Chapters 23–28 selectively but completely enough to understand each technique and its costs.

**Do**
- Build a small typelist algorithm, tuple recursion/pack expansion, mini discriminated-union concept, expression-template toy and template diagnostics lab.

**Videos**
- `Template Metaprogramming: What Is Still Worth Knowing in Modern C++?`
- `How variant Works Conceptually: Storage, Active Alternative, Visitor`
- `Debugging Template Errors Without Reading a 200-Line Error Novel`

**Gate**
Read unfamiliar metaprogramming and simplify it mentally into modern alternatives.

---

# Stage 4 — Standard library mastery

## Unit 085 — Iterators, iterator categories and invalidation

**Read**
- Iterator library — https://en.cppreference.com/w/cpp/iterator
- `iterator_traits` and iterator concepts pages.

**Do**
- Write generic algorithm with category requirements; create invalidation matrix for all containers used later.

**Videos**
- `Iterator Categories: What Algorithms Are Allowed to Assume`
- `Iterator Invalidation: The Table You Need in Your Head`

**Gate**
Predict invalidation after insert/erase/reallocation.

## Unit 086 — vector internals and guarantees

**Read**
- `std::vector` — https://en.cppreference.com/w/cpp/container/vector

**Do**
- Implement educational vector with raw storage, placement construction, growth, move_if_noexcept and exception rollback.

**Videos**
- `How std::vector Actually Grows`
- `I Built vector From Raw Memory`
- `move_if_noexcept: The Hidden Reason vector Sometimes Copies`

**Gate**
Explain size/capacity, invalidation, exception guarantees and relocation.

## Unit 087 — deque, list and forward_list

**Read**
- https://en.cppreference.com/w/cpp/container/deque
- https://en.cppreference.com/w/cpp/container/list
- https://en.cppreference.com/w/cpp/container/forward_list

**Do**
- Benchmark traversal/insertion with controlled workloads; inspect locality.

**Videos**
- `vector vs deque vs list: Big-O Is Not Enough`
- `Why Linked Lists Often Lose on Modern CPUs`

**Gate**
Choose sequence container by access/invalidation/locality needs.

## Unit 088 — map/set and ordered associative containers

**Read**
- `map`, `set`, `multimap`, `multiset` cppreference pages.

**Do**
- Comparator correctness, heterogeneous lookup where supported, node handles.

**Videos**
- `std::map: Ordering, Comparators and Tree Costs`
- `A Bad Comparator Can Break an Associative Container`

**Gate**
Explain strict weak ordering and operation complexity.

## Unit 089 — unordered containers, hashing and load factor

**Read**
- `unordered_map` / `unordered_set` cppreference pages.

**Do**
- Custom hash/equality; reserve/rehash/load-factor experiments; collision stress test.

**Videos**
- `unordered_map Is Not O(1) Magic`
- `Load Factor, Rehashing and Collision Costs`

**Gate**
Explain average vs worst-case behavior and invalidation.

## Unit 090 — std::string and string lifetime/capacity

**Read**
- `basic_string` — https://en.cppreference.com/w/cpp/string/basic_string

**Do**
- Capacity, SSO observation (implementation-specific), iterator/reference invalidation and move/copy experiments.

**Videos**
- `std::string Internals: Capacity, SSO and Invalidation`
- `Moving a String: When Is It Actually Cheap?`

**Gate**
Separate standard guarantees from SSO implementation details.

## Unit 091 — Algorithms, comparators and complexity contracts

**Read**
- Algorithms library — https://en.cppreference.com/w/cpp/algorithm

**Do**
- Implement/reimplement selected `lower_bound`, partition, sort usage; custom comparator/projection-like patterns.

**Videos**
- `The STL Algorithm Mindset: Stop Writing Raw Loops by Default`
- `lower_bound: The Invariant Behind Binary Search`

**Gate**
Choose algorithm from complexity/precondition, not memory of syntax.

## Unit 092 — Callable types: function pointers, functors, std::function, mem_fn, invoke

**Read**
- `<functional>` overview — https://en.cppreference.com/w/cpp/header/functional

**Do**
- Store same callable in each representation; inspect size/allocation/dispatch where relevant.

**Videos**
- `Function Pointer vs Lambda vs std::function`
- `Does std::function Allocate? Let's Measure`

**Gate**
Explain type erasure and ownership/copyability of callable wrappers.

## Unit 093 — tuple, pair, optional, variant and any

**Read**
- `tuple`, `pair`, `optional`, `variant`, `any` cppreference pages.

**Do**
- Variant-based state machine vs virtual hierarchy; optional return, any type erasure, tuple apply/invoke.

**Videos**
- `variant vs Virtual Polymorphism: Same Problem, Different Trade-offs`
- `optional, any and variant: Three Very Different Vocabulary Types`

**Gate**
Choose the right vocabulary type and state lifetime/error implications.

## Unit 094 — Allocators, allocator_traits and PMR

**Read**
- Allocator library — https://en.cppreference.com/w/cpp/memory/allocator
- `allocator_traits` — https://en.cppreference.com/w/cpp/memory/allocator_traits
- PMR — https://en.cppreference.com/w/cpp/memory/memory_resource

**Do**
- Counting allocator; monotonic_buffer_resource experiment; container propagation behavior at a practical level.

**Videos**
- `C++ Allocators: The Layer Under Every STL Container`
- `std::pmr: Changing Allocation Strategy Without Changing Container Type`

**Gate**
Explain allocator vs memory resource and why allocator propagation can affect move complexity.

## Unit 095 — chrono, filesystem, system_error and source-level utilities

**Read**
- `chrono` — https://en.cppreference.com/w/cpp/chrono
- filesystem — https://en.cppreference.com/w/cpp/filesystem
- `system_error` — https://en.cppreference.com/w/cpp/error/system_error

**Do**
- Build file scanner with filesystem + chrono timing + error_code/exception variants.

**Videos**
- `C++ Filesystem: Paths Are Not Just Strings`
- `error_code vs Exception in System APIs`

**Gate**
Use library facilities without unsafe string/time shortcuts.

---

# Stage 5 — C++17 in a linear pass

> Primary source: Nicolai Josuttis, *C++17 — The Complete Guide*. Read the named topic section, then cppreference.

## Unit 096 — Structured bindings, if/switch initializers, inline variables

**Read**
- Josuttis topics: `Structured Bindings`, `if and switch with initializers`, `Inline variables`.
- cppreference pages for each.

**Do**
- Structured-binding reference/copy tests; tuple/array/aggregate cases; inline-variable ODR example.

**Videos**
- `Structured Bindings: Copy or Reference?`
- `Inline Variables Finally Solved a Header Problem`

**Gate**
Predict binding type/lifetime.

## Unit 097 — C++17 evaluation/lambda/aggregate/noexcept/aligned-new changes

**Read**
- Josuttis C++17 Basic Language Features topics: mandatory RVO/materialization, lambda improvements, defined evaluation order, aggregates, noexcept type system, aligned allocation, new attributes.

**Do**
- Version-difference experiments compiled as C++14 vs C++17.

**Videos**
- `C++14 vs C++17: Same Code, Different Language Guarantees`
- `Mandatory Copy Elision Changed What “Return by Value” Means`

**Gate**
State the C++17 rule change, not just current behavior.

## Unit 098 — CTAD, deduction guides and fold expressions

**Read**
- Josuttis Template Improvements topics: CTAD/deduction guides, fold expressions, pack expansion in using declarations, auto NTTPs.

**Do**
- Custom deduction guides and folds over heterogeneous packs.

**Videos**
- `CTAD: When the Class Template Deduces Itself`
- `Fold Expressions Replaced Recursive Variadic Templates`

**Gate**
Write deduction guide/folds without copying syntax.

## Unit 099 — if constexpr, void_t, bool_constant and invoke

**Read**
- Josuttis C++17 template improvements: compile-time if, type-trait improvements, `void_t`, `bool_constant`, `invoke`.

**Do**
- Detection idiom; replace tag/SFINAE branching with if constexpr.

**Videos**
- `The Detection Idiom Before Concepts`
- `if constexpr: Compile-Time Branches That Remove Invalid Code`

**Gate**
Explain discarded statements vs runtime if.

## Unit 100 — optional and variant

**Read**
- Josuttis C++17 chapters/topics for `optional` and `variant` including variant polymorphism.

**Do**
- Parse/result API with optional; state machine with variant + visit.

**Videos**
- `optional: Absence Is Not an Error Code`
- `variant + visit: Closed-World Polymorphism in C++17`

**Gate**
Choose optional/variant vs pointer/inheritance/error object.

## Unit 101 — any, byte and string_view

**Read**
- Josuttis topics: `any`, `byte`, `string_view`, interface design with string_view.

**Do**
- string_view dangling bug zoo; any casts; byte-based buffer.

**Videos**
- `string_view: Zero Copy, Zero Ownership, Plenty of Lifetime Bugs`
- `std::any: Runtime Type Erasure With a Price`

**Gate**
Audit string_view lifetime across API boundaries.

## Unit 102 — filesystem, parallel STL and remaining C++17 library improvements

**Read**
- Josuttis Filesystem chapter/topic and Parallel STL + new algorithms/container improvements.

**Do**
- Filesystem utility; compare `reduce` vs `accumulate` semantics; use execution policies only after understanding constraints.

**Videos**
- `std::reduce Is Not Just Parallel accumulate`
- `C++17 Filesystem: Real Paths, Permissions and Errors`

**Gate**
Know where parallel execution can change assumptions about ordering/side effects.

---

# Stage 6 — C++20 in a linear pass

> Primary source: Nicolai Josuttis, *C++20 — The Complete Guide*.

## Unit 103 — Spaceship operator and comparison rewriting

**Read**
- Josuttis topic: Spaceship Operator.
- `<=>` — https://en.cppreference.com/w/cpp/language/operator_comparison

**Do**
- Strong/weak/partial ordering examples; defaulted comparisons.

**Videos**
- `operator<=>: C++20 Rewrites Comparisons for You`
- `strong_ordering vs partial_ordering: NaN Explains Why`

**Gate**
Choose correct ordering category.

## Unit 104 — Concepts: definitions, requires, subsumption

**Read**
- Josuttis Concepts section: motivation, definitions, requires clauses/expressions, sub-concepts, subsumption, standard concepts.
- cppreference constraints — https://en.cppreference.com/w/cpp/language/constraints

**Do**
- Convert Unit 074 SFINAE APIs to concepts; create ambiguous/subsumed overloads.

**Videos**
- `C++20 Concepts: Templates Finally Get Readable Constraints`
- `requires Expressions vs requires Clauses`
- `Concept Subsumption: Which Constrained Overload Wins?`

**Gate**
Design a concept that checks semantics without overconstraining implementation.

## Unit 105 — Ranges fundamentals, views and pipelines

**Read**
- Josuttis Ranges and Views: motivation, views, projections, adaptors, lazy evaluation.
- cppreference ranges — https://en.cppreference.com/w/cpp/ranges

**Do**
- Build pipelines; mutate through views; compare eager container creation.

**Videos**
- `C++20 Ranges: Algorithms Without begin/end Boilerplate`
- `Views Are Lazy—and That Changes Everything`

**Gate**
Explain range vs view and evaluation timing.

## Unit 106 — Range lifetime, borrowed ranges, sentinels and const traps

**Read**
- Josuttis Ranges details: sentinels, borrowed ranges, dangling, const issues, prvalues, limitations.

**Do**
- Create dangling-view examples; test borrowed_range and prvalue pipelines.

**Videos**
- `The C++20 View That Dangled`
- `Borrowed Ranges: The Lifetime Concept Behind Safe Iterators`

**Gate**
Audit range pipeline lifetime before running it.

## Unit 107 — span and non-owning contiguous APIs

**Read**
- `std::span` — https://en.cppreference.com/w/cpp/container/span
- Josuttis ranges/spans material.

**Do**
- Replace pointer+size APIs with span; const/mutable span and subspan experiments.

**Videos**
- `std::span: A Pointer and Size With Better Semantics`
- `span Does Not Own Memory—Lifetime Still Matters`

**Gate**
Use span only where contiguous borrowed lifetime is valid.

## Unit 108 — Coroutines: language transformation and handles

**Read**
- Josuttis Coroutines: introduction, coroutine interfaces/handles, promise types, `co_await`, `co_yield`, `co_return`.
- cppreference coroutines — https://en.cppreference.com/w/cpp/language/coroutines

**Do**
- Build tracer that logs creation, initial suspend, resume, final suspend and destruction.

**Videos**
- `C++ Coroutines: What the Compiler Builds Around co_await`
- `I Traced Every Suspend and Resume in a Coroutine`

**Gate**
Draw coroutine frame/promise/handle lifetime.

## Unit 109 — Coroutines advanced: awaiters, exceptions, memory and transfer

**Read**
- Josuttis advanced coroutine topics: awaitable/awaiter, symmetric transfer, exceptions, memory management, `await_transform`, coroutine traits.

**Do**
- Educational Task/Generator type; custom awaiter; inject exception; observe allocation.

**Videos**
- `Awaiter vs Awaitable vs Promise: The Coroutine Vocabulary`
- `Who Allocates the Coroutine Frame?`

**Gate**
Explain control flow and ownership without framework magic.

## Unit 110 — Modules

**Read**
- Josuttis Modules: interface/implementation units, partitions, global/private fragments, headers, practical compiler usage.
- cppreference modules — https://en.cppreference.com/w/cpp/language/modules

**Do**
- Build a small module with interface + implementation + partition if your compiler/toolchain supports it.

**Videos**
- `C++20 Modules: Not Just Faster Headers`
- `Building a Real Module With GCC/Clang/MSVC Support Caveats`

**Gate**
Explain visibility vs reachability and migration constraints.

## Unit 111 — jthread, stop_token, latch, barrier, semaphore

**Read**
- Josuttis Multi-Threading and Concurrency Features section.
- cppreference pages for each primitive.

**Do**
- Cancellation with jthread; phased worker with barrier; resource pool with semaphore.

**Videos**
- `std::jthread Fixed a Dangerous std::thread Default`
- `Latch vs Barrier vs Semaphore: Pick the Right Primitive`

**Gate**
API-level competence only; deep concurrency correctness belongs to Curriculum 02.

## Unit 112 — atomic_ref and C++20 atomic additions

**Read**
- `atomic_ref` — https://en.cppreference.com/w/cpp/atomic/atomic_ref
- Josuttis concurrency additions.

**Do**
- Apply atomic_ref to suitably aligned object; document lifetime/alignment requirements.

**Videos**
- `atomic_ref: Atomic Operations Without Changing the Stored Type`
- `The Alignment and Aliasing Rules atomic_ref Requires`

**Gate**
Know when atomic_ref is valid; defer memory-order mastery to Curriculum 02.

## Unit 113 — consteval, constinit and expanded constexpr

**Read**
- Josuttis compile-time features.
- `consteval` / `constinit` / `constexpr` cppreference pages.

**Do**
- Compare runtime-callable constexpr, immediate consteval and initialization-only constinit.

**Videos**
- `constexpr vs consteval vs constinit`
- `Compile-Time vector/string: What C++20 Actually Allows`

**Gate**
Choose correct compile-time facility by guarantee required.

## Unit 114 — C++20 lambdas, aggregates, attributes and small core features

**Read**
- Josuttis `Other core features`: lambda extensions, enum using declarations, conditional explicit, char8_t, range-for initializer, likely/unlikely, no_unique_address, nodiscard messages, aggregate changes.

**Do**
- One minimal experiment per feature; compare layout with `[[no_unique_address]]`.

**Videos**
- `[[no_unique_address]]: The Attribute That Can Shrink Objects`
- `conditional explicit: One Constructor, Two Conversion Policies`

**Gate**
Know what changed and where it affects API/ABI/layout.

## Unit 115 — Formatting, chrono/calendar and library additions

**Read**
- Josuttis C++20 formatted output and chrono sections.
- cppreference `<format>` and chrono calendar/time-zone pages.

**Do**
- Type-safe formatting; calendar/time-zone examples if implementation supports them.

**Videos**
- `std::format: Type-Safe Formatting in C++`
- `C++20 chrono Finally Learned Calendars and Time Zones`

**Gate**
Use facility correctly and know implementation-support caveats.

---

# Stage 7 — C++23 in a linear pass

> Primary source: Nicolai Josuttis, *C++23 — The Complete Guide* / his C++23 topic sequence, plus current cppreference.

## Unit 116 — expected and monadic error handling

**Read**
- `std::expected` — https://en.cppreference.com/w/cpp/utility/expected
- Josuttis topic: `std::expected<>` and monadic operations for optional/expected.

**Do**
- Parse/config API with expected; chain `and_then`/`transform`/error path where supported.

**Videos**
- `std::expected: Return a Value or a Real Error Type`
- `Monadic expected: Chaining Without Exception or Error-Code Boilerplate`

**Gate**
Compare exceptions, error_code, optional and expected.

## Unit 117 — move_only_function and forward_like

**Read**
- `std::move_only_function` and `std::forward_like` cppreference pages.

**Do**
- Move-only callback owning unique_ptr; forwarding members with forward_like.

**Videos**
- `move_only_function: std::function for Move-Only Callables`
- `forward_like: Forward With Someone Else's cv-ref Qualifiers`

**Gate**
Explain why std::function's copyability can be wrong for ownership-heavy callbacks.

## Unit 118 — mdspan

**Read**
- `std::mdspan` — https://en.cppreference.com/w/cpp/container/mdspan
- Josuttis topic: mdspan.

**Do**
- 2D/3D view over flat memory; layout/stride mapping experiment.

**Videos**
- `mdspan: Multidimensional Views Without Owning Memory`
- `Row-Major, Column-Major and Strides With mdspan`

**Gate**
Separate storage ownership from multidimensional indexing/layout.

## Unit 119 — print/println and stacktrace

**Read**
- `std::print` / `std::println` and `std::stacktrace` cppreference pages.
- Josuttis formatted-output and stacktrace topics.

**Do**
- Logging/demo tool using format/print; capture stacktrace on controlled error if implementation supports it.

**Videos**
- `std::print: C++ Finally Has a Modern Hello World`
- `std::stacktrace: Debug Context as a Standard-Library Type`

**Gate**
Know portability/implementation support in your toolchain.

## Unit 120 — Deducing this / explicit object parameters

**Read**
- Explicit object member functions — https://en.cppreference.com/w/cpp/language/member_functions#Explicit_object_member_functions
- Josuttis topic: Deducing this.

**Do**
- Remove duplicated const/non-const/ref-qualified member overloads; recursive lambda example.

**Videos**
- `Deducing this: The Feature That Changes Member Functions`
- `One Function for const&, &, and && With Explicit Object Parameters`

**Gate**
Explain how explicit object parameter changes deduction and overload design.

## Unit 121 — if consteval, range-for lifetime fix, static call/subscript operators

**Read**
- Josuttis topics: `if consteval`, fixed range-based for loop, static operators/recursive lambdas, other core updates.
- cppreference C++23 language support pages.

**Do**
- Compile selected examples in C++20 vs C++23.

**Videos**
- `if consteval: Detect Immediate Evaluation Cleanly`
- `C++23 Fixed a Range-for Lifetime Trap`

**Gate**
Know which problems are version fixes rather than new patterns to memorize.

## Unit 122 — C++23 ranges/views, ranges::to and generator

**Read**
- Josuttis C++23 ranges/views + `ranges::to` + generator topics.
- Current cppreference ranges pages.

**Do**
- Compose new views, materialize with ranges::to where supported, simple generator.

**Videos**
- `ranges::to: Finally Materialize a View Cleanly`
- `std::generator: Coroutines Meet Ranges`

**Gate**
Understand lifetime and lazy/eager transition.

## Unit 123 — flat containers and remaining practical C++23 library additions

**Read**
- Josuttis topic: flat sets/maps and remaining library updates.
- cppreference C++23 library features index — https://en.cppreference.com/w/cpp/23

**Do**
- Compare flat_map conceptually/experimentally with map/unordered_map where implementation supports it.

**Videos**
- `flat_map: Sorted Contiguous Storage vs Tree-Based map`
- `Which C++23 Features Matter to Systems Programmers?`

**Gate**
Be able to discuss support status instead of assuming every production compiler/library has everything.

---

# Stage 8 — Toolchain, ABI, debugging and production C++

## Unit 124 — Preprocessor, headers, CMake and reproducible builds

**Read**
- CMake official tutorial — https://cmake.org/cmake/help/latest/guide/tutorial/
- Revisit translation phases.

**Do**
- Multi-target CMake project, warnings, sanitizers, Debug/Release, compile_commands.json.

**Videos**
- `CMake Without Cargo Cult: Targets, Includes and Libraries`
- `What the C++ Preprocessor Actually Does Before Compilation`

**Gate**
Build project from terminal without IDE magic.

## Unit 125 — Static libraries, shared libraries and symbol inspection

**Read**
- GCC/Clang docs as needed; Linux `nm`, `readelf`, `objdump`, `ldd` man pages.

**Do**
- Build `.a` and `.so`; inspect symbols/dependencies; break/fix missing symbol and visibility cases.

**Videos**
- `Static vs Shared Libraries: What the Linker Actually Produces`
- `Reading C++ Symbols With nm, readelf and objdump`

**Gate**
Diagnose link/load failure from command-line evidence.

## Unit 126 — Name mangling, ABI, vtables and binary compatibility

**Read**
- Itanium C++ ABI relevant sections — https://itanium-cxx-abi.github.io/cxx-abi/abi.html
- Compiler docs for your platform.

**Do**
- Inspect mangled names, layout/vtables; deliberately break ABI by changing public class layout; compare PImpl.

**Videos**
- `C++ ABI: Why Changing a Private Member Can Break Binary Compatibility`
- `Name Mangling and vtables: Reading the Binary`

**Gate**
Separate standard language guarantees from ABI implementation conventions.

## Unit 127 — gdb/lldb and core-dump debugging

**Read**
- GDB manual selected commands: break, watch, bt, frame, threads, disassemble.

**Do**
- Debug crash with symbols; core dump; watchpoint; multi-thread backtrace preview.

**Videos**
- `Debugging a C++ Crash From a Core Dump`
- `Watchpoints: Catch the Exact Write That Corrupted Memory`

**Gate**
Find a seeded crash without print-debugging.

## Unit 128 — ASan, UBSan, LSan and TSan awareness

**Read**
- Clang sanitizer docs — https://clang.llvm.org/docs/

**Do**
- Seed UAF, OOB, leak, UB and data race; run relevant sanitizer and interpret report.

**Videos**
- `I Created Five C++ Memory Bugs and Let ASan Find Them`
- `UBSan Finds Bugs That “Work” in Debug Builds`

**Gate**
Read sanitizer traces and identify root cause, not just failing line.

## Unit 129 — Compiler Explorer, optimization reports and assembly literacy

**Read**
- Compiler Explorer — https://godbolt.org/
- GCC/Clang optimization-report docs as needed.

**Do**
- Compare -O0/-O2/-O3, copies/moves, virtual calls, templates, vectorization examples.

**Videos**
- `Compiler Explorer: My Second Monitor for Learning C++`
- `What -O2 Actually Changed in This C++ Function`

**Gate**
Read basic loads/stores/calls/branches and correlate with source; full performance depth comes later.

## Unit 130 — Testing: unit, property, fuzz and compile-fail tests

**Read**
- GoogleTest docs — https://google.github.io/googletest/
- libFuzzer docs — https://llvm.org/docs/LibFuzzer.html

**Do**
- Unit tests + death/error cases + fuzz parser + compile-fail/static_assert suite for template constraints.

**Videos**
- `Testing C++ Beyond Unit Tests`
- `Fuzzing a C++ Parser Until It Crashes`

**Gate**
Choose test style based on failure mode.

## Unit 131 — API design with ownership, views, errors and polymorphism

**Read**
- C++ Core Guidelines: interfaces, resource management, classes, errors.
- Revisit relevant Iglberger later in architecture curriculum; here focus on C++-level API semantics.

**Do**
- Design one library API three ways; document ownership, lifetime, error and ABI contracts.

**Videos**
- `A Good C++ API Makes Ownership Obvious`
- `Value, Reference, span, string_view, unique_ptr: What Should an API Take?`

**Gate**
A reviewer can identify ownership/lifetime without reading implementation.

## Unit 132 — C++ capstone library

**Read**
- No new broad reading. Reuse exact sources above only as needed.

**Do**
Build one polished library containing several of:
- value types + RAII resource handle
- generic/constrained API
- vector/allocator experiment or container-backed subsystem
- type-erased/runtime-polymorphic boundary
- PImpl public API
- tests, sanitizers, benchmarks and CMake
- ABI/versioning note

**Videos**
- `Building a Production-Style Modern C++ Library From Zero`
- `Full Code Review: Ownership, Templates, ABI, Tests and Performance`

**Gate**
You can defend every public API and implementation trade-off.

---

# Stage 9 — Final C++ interview conversion gate

## Unit 133 — 200 code-prediction questions

**Do**
Create/solve 200 mixed questions covering:
- initialization
- conversions/overloads
- lifetime
- special members
- deduction/decltype
- move/forwarding
- templates
- STL invalidation
- exceptions/noexcept
- C++17/20/23 features

**Pass**
≥90% after spaced review, not immediately after reading.

**Video**
- `200 Modern C++ Code-Prediction Questions: What I Got Wrong`

## Unit 134 — Implement-from-memory day

**Do without notes**
- RAII file/fd handle
- simplified unique_ptr
- simplified vector growth core
- LRU cache
- perfect-forwarding wrapper
- constrained generic algorithm
- variant visitor/state machine
- PImpl library skeleton

**Pass**
Correct ownership/lifetime/exception behavior and tests.

**Video**
- `I Rebuilt My Core C++ Toolkit Without Looking Anything Up`

## Unit 135 — Debugging and code-review day

**Do**
- Seed 20 bugs: UB, lifetime, ownership, iterator invalidation, bad move, template misuse, ABI/API issue.
- Diagnose with warnings/sanitizers/gdb/Compiler Explorer.

**Pass**
Find root causes and explain preventive design rule.

**Video**
- `20 Senior C++ Bugs: Debug Them With Me`

## Unit 136 — Full Staff/Senior C++ mock

**Format**
- 20 min language/lifetime.
- 20 min templates/generic programming.
- 15 min STL/API design.
- 15 min debugging/toolchain/ABI.
- 20–30 min coding/design problem.

**Pass**
No major conceptual hole; answers remain precise under follow-up questions. Any failed area sends you back to its exact unit.

**Videos**
- `Full Staff C++ Mock Interview—No Trivia, Only Reasoning`
- `What I Would Ask a Senior C++ Engineer in 90 Minutes`

---

# Source index

Use these repeatedly; do not collect random courses unless a listed source fails to explain a specific concept.

1. Scott Meyers — *Effective Modern C++* — **all 42 items**.
2. cppreference — exact language/library reference: https://en.cppreference.com/w/
3. C++ Core Guidelines — https://isocpp.github.io/CppCoreGuidelines/CppCoreGuidelines
4. Nicolai Josuttis — *C++ Move Semantics: The Complete Guide*.
5. Vandevoorde/Josuttis/Gregor — *C++ Templates: The Complete Guide, 2nd Edition*.
6. Nicolai Josuttis — *C++17: The Complete Guide*.
7. Nicolai Josuttis — *C++20: The Complete Guide*.
8. Nicolai Josuttis — *C++23: The Complete Guide* / current C++23 material.
9. Josuttis — *The C++ Standard Library* as optional deeper library reading; cross-check version-sensitive behavior with cppreference.
10. Compiler Explorer, GCC, Clang, gdb/lldb, sanitizers, CMake, GoogleTest and libFuzzer.

# Content rule

The video titles above are **minimum core videos**, not a cap. If Unit 036 (`unique_ptr`) produces six excellent videos—internals, implementation, deleters, arrays, PImpl and interview questions—make all six. Do not combine them merely to maintain a schedule.

# Final meaning of “Curriculum 01 complete”

You are done only when:
- Scott 1–42 can be explained without rereading.
- Modern C++17/20/23 features above are usable, not merely recognizable.
- Templates and STL are strong enough to reason about unfamiliar generic code.
- Lifetime/ownership/exception safety are automatic code-review instincts.
- You can debug from compiler/sanitizer/debugger evidence.
- You can discuss ABI/toolchain issues at a practical systems-engineering level.
- You pass Units 133–136.

Then move to **Curriculum 02 — Concurrency and the C++ Memory Model**.