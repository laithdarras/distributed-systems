# Lecture 2 – Distributed Systems Overview

## What is Distributed Computing?
- **Definition (informal):** Running an application across multiple nodes that coordinate to solve a problem.
- **Definition (formal):** A collection of independent hardware/software components, networked and coordinated via **message passing**, **RPCs**, or **events**.
- **Examples:**  
  - Search engines (Google, Brave)  
  - Social networks (Instagram, LinkedIn)  
  - Cloud/datacenter providers (Amazon, Alibaba)

> **Tanenbaum & Steen:** *“A distributed system is a collection of autonomous computing elements that appears to its users as a single coherent system.”*

---

## Goals of Distributed Systems
- **Transparency:** Hide complexity from the user (distribution, replication, failover).  
- **Scalability:** Support millions of requests with low latency.  
- **Efficiency:** Optimize performance and resource usage.  
- **Manageability:** Monitor, update, and tolerate faults.  
- **Openness:** Programmable, interoperable, portable, extensible.

---

## Key Concepts
- **Node:** Software or hardware component.  
- **Resource:** Asset such as a file, service, or TCP connection.  
- **Overlay Network:** Logical communication structure connecting nodes.  
- **Middleware:** A software layer across nodes providing transparency and consistency.  
- **Concurrency:** Multiple operations/tasks executed in parallel (needs synchronization).  
- **State:** Represents current system status (local vs. global).

---

## Multi-Tier System Architecture
- **Tier 1 – Web Servers:** Request handling, load balancing, fault tolerance.  
- **Tier 2 – Cache Servers:** In-memory caching for fast access.  
- **Tier 3 – Databases/Data Centers:** Persistent storage and heavy computation.  

---

## Data Center Structure

- **Servers:** CPUs, cache, DRAM, disks.  
- **Racks:** Groups of servers connected via rack switches.  
- **Data Center Switches:** Interconnect racks.  
- **Support:** Cooling + power infrastructure.  
- **User Interfaces:** Web browsers, mobile apps, CLI/GUI, REST services.

---

## Why Do We Need Distributed Systems?
- Support **resource sharing** and transparency.  
- Provide a single coherent system to users.  
- Enable **scalability** and fault tolerance for large-scale applications.  
- Common use cases: search engines, databases, online services, cloud applications.

---

## Types of Distributed Systems
1. **High-Performance Distributed Computing (HPC):**
   - Cluster → Grid → Cloud computing.
   - Used for parallel execution of scientific and engineering problems.
2. **Distributed Information Systems:**
   - Databases, enterprise application integration, data warehouses.
3. **Pervasive/Embedded Systems:**
   - IoT devices, wireless sensor networks, mobile computing, GPS.

---

## Parallel Computing (HPC)
- **Definition:** A type of computation where many calculations are executed simultaneously.
- **Principle:** Large problems are decomposed into smaller subproblems that can run in parallel.
- **Execution:** Multi-/many-core CPUs, GPUs, HPC clusters.

### Architectures & Memory Models
- **UMA (Uniform Memory Access):** Equal latency for all memory access.  
- **NUMA (Non-Uniform Memory Access):** Different latencies across memory modules.  
- **RDMA (Remote Direct Memory Access):** Direct memory access across nodes.  
- **DSM (Distributed Shared Memory):** Memory abstraction across multiple machines.

### Programming Models
- **BSP (Bulk Synchronous Parallel)**  
- **MPI (Message Passing Interface)**  
- **LogP/LogGP models** 

---

## Parallel vs. Distributed Computing
| Aspect           | Parallel Computing                | Distributed Computing             |
|------------------|-----------------------------------|-----------------------------------|
| **Focus**        | Performance, scalability (science)| Resource sharing, reliability (industry) |
| **Processors**   | Brawny + accelerators (GPUs)      | Mix of wimpy/brawny processors    |
| **Memory**       | Tightly coupled (shared memory)   | Loosely coupled (distributed)     |
| **Interconnect** | High-speed InfiniBand, RDMA       | Ethernet, wireless, TCP/IP        |
| **Consistency**  | Strong                            | Varied                            |

---

## Scaling and Performance

### Strong Scaling (Amdahl’s Law)
- **Definition:** Fix problem size, increase processors to reduce execution time.
- **Formula:**  
  \( T(N) = T(1)(s + \frac{p}{N}) \)  
  \( S(N) = \frac{1}{s + p/N} \)  
- **Implication:** Speedup is limited by the serial fraction \( s \).  

### Weak Scaling (Gustafson’s Law)
- **Definition:** Fix workload per processor, increase processors to handle more work.
- **Formula:**  
  \( \text{Scaled Speedup} = s + p \times N \)  
- **Implication:** Optimistic view—no theoretical upper bound on speedup.

---

## Challenges in Distributed Systems
- **Problem decomposition:** Hard to split sequential tasks.  
- **Correctness:** More failure modes and concurrency errors.  
- **Granularity:** Parallelism ranges from bit-level to datacenter-level.  
- **Resource management:** Assigning tasks, scheduling, data sharing, fault recovery.  
- **Congestion:** Analogous to traffic management; bottlenecks must be avoided.

---

## Summary / Takeaways
- Distributed systems = independent nodes working together, appearing as **one coherent system**.  
- Goals: **transparency, scalability, efficiency, openness, manageability.**  
- Common architecture: **web servers → caches → databases/datacenters.**  
- **HPC and parallel computing** underpin modern distributed systems.  
- **Scaling laws (Amdahl & Gustafson)** explain performance limits and trade-offs.  