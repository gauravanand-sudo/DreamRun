# DreamRun Roadmap — Weeks 25-30

## Week 25 — Linux process model, syscalls, fork/exec, signals, scheduling
**Phase:** Linux Systems & Networking  
**Dates:** 2027-01-25 to 2027-01-31  
**Read:** CS:APP exceptional control flow/processes. Linux man pages fork, execve, waitpid, signal, clone conceptually.  
**Build / break / measure:** Write process launcher, fork/exec pipeline, signal handling, child reaping. Compare process/thread costs carefully. Use strace to observe syscalls.  
**Mastery gate:** Explain process vs thread resources, fork copy-on-write concept, exec, zombie/orphan, signals and syscall boundary.  
**DSA:** DP on subsequences  
**Video A:** What Linux Actually Does When You Start a Process  
**Video B:** I Rebuilt a Tiny Shell to Understand fork and exec

## Week 26 — Virtual memory, mmap, files, page faults and file I/O
**Phase:** Linux Systems & Networking  
**Dates:** 2027-02-01 to 2027-02-07  
**Read:** CS:APP virtual memory/system I/O. man pages mmap, munmap, mprotect, read/write, pread/pwrite, fsync.  
**Build / break / measure:** Build mmap file reader and regular read baseline. Trigger page faults, inspect /proc maps, compare buffered patterns. Create simple append-only log.  
**Mastery gate:** Explain address spaces, page tables/TLB concept, mmap semantics, page faults, file descriptors and durability caveats.  
**DSA:** DP on grids  
**Video A:** Virtual Memory for C++ Engineers — Not the Textbook Version  
**Video B:** mmap vs read: I Benchmarked File I/O and Watched Page Faults

## Week 27 — Sockets, addressing, TCP lifecycle and protocol design
**Phase:** Linux Systems & Networking  
**Dates:** 2027-02-08 to 2027-02-14  
**Read:** Beej sections on sockets, IP, ports, byte order, connect/bind/listen/accept/send/recv. man pages socket/bind/listen/accept/connect.  
**Build / break / measure:** Build blocking TCP echo server/client, then framed binary message protocol. Capture packets with tcpdump/Wireshark if available. Test partial reads/writes.  
**Mastery gate:** Explain TCP byte stream vs messages, connection lifecycle, byte order, framing, partial IO and backpressure beginnings.  
**DSA:** DP mixed  
**Video A:** What Actually Happens When C++ Calls socket()?  
**Video B:** Building a TCP Server and Breaking Message Framing

## Week 28 — UDP, multicast, serialization and reliability trade-offs
**Phase:** Linux Systems & Networking  
**Dates:** 2027-02-15 to 2027-02-21  
**Read:** Beej UDP/datagram sections. man pages sendto/recvfrom/ip multicast options. Read endianness/alignment references.  
**Build / break / measure:** Build UDP publisher/subscriber and custom binary packet format. Add sequence numbers, loss detection, replay stub. Add multicast if local setup permits.  
**Mastery gate:** Explain datagram semantics, loss/reordering/duplication, multicast use, serialization, alignment and network byte order.  
**DSA:** Graph + DP mix  
**Video A:** TCP vs UDP: The Explanation Systems Interviews Want  
**Video B:** I Built a Tiny Multicast Market-Data Feed

## Week 29 — Nonblocking I/O, select/poll/epoll and reactor design
**Phase:** Linux Systems & Networking  
**Dates:** 2027-02-22 to 2027-02-28  
**Read:** Beej nonblocking/select concepts; Linux man pages fcntl, select, poll, epoll. Read edge vs level triggering carefully.  
**Build / break / measure:** Evolve server: blocking -> thread-per-client -> thread pool -> nonblocking epoll. Load-test with local clients. Handle partial writes and connection state.  
**Mastery gate:** Explain readiness vs completion, level vs edge triggered, thundering herd concept, backpressure and connection state machines.  
**DSA:** Sliding/two-pointer mixed  
**Video A:** select vs poll vs epoll: Why Linux Needed Three APIs  
**Video B:** Building an epoll Server From Scratch — No Frameworks

## Week 30 — Linux/network profiling capstone: high-performance KV server
**Phase:** Linux Systems & Networking  
**Dates:** 2027-03-01 to 2027-03-07  
**Read:** Brendan Gregg networking/CPU observability reference. Review Beej/man pages. Read system-call docs used.  
**Build / break / measure:** Build CppValley KV v1: epoll server, binary protocol, in-memory map, worker strategy, metrics, graceful shutdown, load generator. Profile CPU/syscalls and write design doc.  
**Mastery gate:** Systems/network mock >=80%. Explain blocking points, failure modes, p99 latency investigation and why chosen architecture fits workload.  
**DSA:** Heap/interval mixed  
**Video A:** I Load-Tested My C++ Server Until It Collapsed  
**Video B:** From Flame Graph to Fix: Profiling a C++ Network Server
