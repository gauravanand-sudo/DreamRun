# DreamRun Roadmap — Weeks 43-48

## Week 43 — Data systems trade-offs, storage engines, replication basics
**Phase:** Distributed Systems & Google-Style Design  
**Dates:** 2027-05-31 to 2027-06-06  
**Read:** DDIA 2e: architecture trade-offs and storage/data-model foundations; Alex Xu only after reading fundamentals.  
**Build / break / measure:** Extend KV with append-only log + recovery. Add primary/follower replication prototype over TCP. Simulate follower lag.  
**Mastery gate:** Explain log vs snapshot concept, replication lag, durability vs latency, system-of-record vs derived data and single-node vs distributed trade-offs.  
**DSA:** Unseen medium: mixed 1  
**Video A:** Why Distributed Systems Get Hard After the Second Machine  
**Video B:** I Added Replication to My C++ KV Store — Then Broke It

## Week 44 — Partitioning, consistent hashing, caching and load balancing
**Phase:** Distributed Systems & Google-Style Design  
**Dates:** 2027-06-07 to 2027-06-13  
**Read:** DDIA partitioning/caching-related chapters/sections. Alex Xu consistent-hashing/cache cases for interview framing.  
**Build / break / measure:** Implement consistent-hash ring simulation; shard keys across nodes/processes; add simple client routing and rebalance experiment.  
**Mastery gate:** Explain hot keys, rebalance cost, virtual nodes concept, cache invalidation, load balancing and why uniform hashing isn't enough.  
**DSA:** Unseen medium: mixed 2  
**Video A:** Consistent Hashing Without the Hand-Wavy Circle Diagram  
**Video B:** I Sharded a KV Store and Created a Hot-Key Disaster

## Week 45 — Consistency, quorums, transactions, idempotency and retries
**Phase:** Distributed Systems & Google-Style Design  
**Dates:** 2027-06-14 to 2027-06-20  
**Read:** DDIA consistency/transactions chapters. Alex Xu payment/idempotency-style examples if owned.  
**Build / break / measure:** Create retrying client where response loss causes duplicate operation; add request IDs/idempotency. Simulate read/write quorum on in-memory replicas.  
**Mastery gate:** Explain at-least-once effects, idempotency, linearizability concept, eventual consistency, quorum intuition and transaction boundaries.  
**DSA:** Unseen medium: mixed 3  
**Video A:** Retries Can Corrupt Your System  
**Video B:** I Made a Duplicate-Write Bug, Then Designed Idempotency

## Week 46 — Logs, queues, streams and backpressure
**Phase:** Distributed Systems & Google-Style Design  
**Dates:** 2027-06-21 to 2027-06-27  
**Read:** DDIA event/log/stream chapters. Review bounded queues and network backpressure.  
**Build / break / measure:** Build append-only event log + consumer offsets; bounded producer/consumer pipeline; overload it and implement backpressure/drop/retry policy.  
**Mastery gate:** Explain queue vs log, consumer offset, replay, backpressure, overload collapse, delivery semantics and ordering.  
**DSA:** Unseen medium: mixed 4  
**Video A:** Queues Don't Fix Overload — They Hide It  
**Video B:** I Overloaded My Pipeline Until Backpressure Saved It

## Week 47 — Leader election, consensus concepts, failure detection and time
**Phase:** Distributed Systems & Google-Style Design  
**Dates:** 2027-06-28 to 2027-07-04  
**Read:** DDIA consensus/failures chapters. Read Raft paper/visualization optionally for concepts; do not spend week building production Raft.  
**Build / break / measure:** Build simplified deterministic leader-election simulation or integrate existing conceptual state machine; simulate partitions, delayed messages and split-brain safeguards.  
**Mastery gate:** Explain why distributed consensus exists, term/epoch concept, majority, failure detector limitations, clocks/timeouts and split-brain risk.  
**DSA:** Unseen medium: mixed 5  
**Video A:** Leader Election: Why 'Just Pick Another Server' Fails  
**Video B:** I Simulated Network Partitions to Understand Consensus

## Week 48 — Distributed KV capstone + Google system-design conversion
**Phase:** Distributed Systems & Google-Style Design  
**Dates:** 2027-07-05 to 2027-07-11  
**Read:** Review DDIA; Alex Xu Vol 1/2 selected cache, rate limiter, feed/storage designs. Google current Staff infra competency checklist.  
**Build / break / measure:** Finalize CppValley KV: persistence, replication, sharding prototype, retries/idempotency, metrics, failure test plan. Run two 60-minute system-design mocks.  
**Mastery gate:** Can drive ambiguous system design: requirements, estimates, API/data model, high-level design, bottlenecks, failures, consistency, evolution, observability.  
**DSA:** Timed coding mock  
**Video A:** Design a Distributed Cache: Full Staff-Level Walkthrough  
**Video B:** I Killed Nodes During Writes — Here's What My Design Got Wrong
