---
sidebar_position: 1
---
# Virtual Threads
This page explains the `system.useVirtualThreads` option in YueMi-Spigot and its trade-offs.

## Comparison Table

| Feature                          | Virtual Threads (YueMi) | Thread Pool (Paper) |
|----------------------------------|--------------------------|----------------------|
| **Minimum Threads Alive**        | 0 (spawn on demand)      | 4 core threads kept alive |
| **Idle Thread Keep-Alive**       | ~10s                     | ~30s                 |
| **Scaling Behavior**             | Up to tens of thousands of tasks | Limited by physical threads |
| **Best For**                     | I/O-bound tasks (DB, HTTP, disk) | Mixed workloads, stable under CPU load |
| **Memory Overhead per Thread**   | Very low (KBs)           | Higher (MBs)         |
| **CPU-bound Workloads**          | No real advantage        | Predictable & stable |
| **Compatibility**                | Newer (Java 21+, may expose plugin issues) | Mature and widely tested |
| **Resource Efficiency**          | Very high                | Moderate             |

## Pros of Virtual Threads
- Extremely lightweight; can handle massive concurrency.  
- Great for async plugins that perform database, network, or file operations.  
- Frees server owners from tuning thread pool sizes.

## Trade-offs
- Still a newer JVM feature; some plugins may not be fully compatible.  
- No performance boost for CPU-heavy async tasks.  
- May reveal concurrency bugs in poorly written plugins.