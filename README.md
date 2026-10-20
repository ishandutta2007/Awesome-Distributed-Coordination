# Awesome-Distributed-Coordination

## Top Distributed Coordination Ecosystem



**Curated List of SaaS Products & Open-Source GitHub Projects**  

*Focused on Consensus Protocols, Service Discovery & Distributed Configuration*  

**Last updated: October 2026**



This repository tracks notable **SaaS platforms** and **open-source projects** for **Distributed Coordination**. These tools enable distributed systems to agree on state—electing leaders, storing configuration, discovering services, and coordinating locks across multiple nodes—without a single point of failure.



**Examples** include etcd, Apache ZooKeeper, HashiCorp Consul, Redis, CoreDNS, Hazelcast, Kuma, and Eureka (the category leaders).



**Open-source emphasis**: This section is heavily expanded with every major active project for self-hosting, consensus protocols, and open service discovery—ideal for platform engineers, SREs, and organizations seeking transparent, vendor-independent distributed infrastructure.



Contributions welcome! Open a PR to add/update entries. Keep descriptions factual and link to official sites.



## Table of Contents

- [SaaS/Hosted Platforms](#saas-hosted-platforms)

- [Open-Source GitHub Projects](#open-source-github-projects)

- [How to Contribute](#how-to-contribute)

- [Disclaimer](#disclaimer)



## SaaS/Hosted Platforms



- **Redis Enterprise**

  **Commercial version of Redis** with active-active geo-distribution, built-in CRDTs, and enterprise support. **Free tier**: **Redis Cloud Free** provides 30MB storage with limited connections; **Fixed plans start at $5/month** for 250MB. **Best for**: organizations wanting Redis with commercial support and multi-region replication.



- **Chubby (Google)**

  **Google's internal lock service**—the inspiration for many coordination systems. **Note**: Not publicly available. **The historical benchmark** against which all distributed lock services are measured.



- **AWS AppConfig / Azure App Configuration / Google Cloud Runtime Configurator**

  Managed configuration services with versioning, validation, and gradual rollouts. **Best for**: cloud-native applications wanting managed config without operating a coordination cluster.



## Open-Source GitHub Projects



- **etcd**

  **A distributed reliable key-value store for the most critical data of a distributed system** (Apache-2.0) — **the Kubernetes standard** . **The primary datastore for Kubernetes**—every cluster state write flows through etcd. **Raft consensus** with strong consistency guarantees. **Features**: **watch for key changes**, **leases for TTL-based expiration**, **transactions**, **RBAC**, and **snapshot/restore** for backups. **The reference implementation for distributed configuration**—**choose when you need strong consistency and the Kubernetes ecosystem** .



- **Apache ZooKeeper**

  **Centralized service for maintaining configuration information, naming, providing distributed synchronization, and providing group services** (Apache-2.0) — **the battle-tested veteran** . **ZooKeeper 3.9** brings major upgrades—**pluggable metrics system** to track and expose server and client metrics, **new Prometheus metrics endpoint**, **extended 'snapshot' and 'restore' commands** for moving server state to new hosts (with experimental support for logical quorum changes), and **new 'whoami' command** to display authentication details . **The reference implementation for consensus and coordination**—**choose when you need mature leader election, locks, and configuration with a proven track record** .



- **HashiCorp Consul**

  **Service networking platform** (BUSL-1.1 for enterprise features) — **the service discovery and mesh choice** . **Features**: **service discovery via DNS or HTTP API**, **health checking**, **KV store**, **intentions for service-to-service authorization**, and **multi-datacenter federation**. **Consul 2.0** adds **multi-port service mesh support** (beta, Enterprise), **CyberArk Workload Identity Manager as external CA**, **global RPC rate limiting**, and **API gateway auto-scaling** . **The reference implementation for service discovery**—**choose when you need DNS-based discovery alongside KV storage and mesh capabilities** .



- **Redis**

  **In-memory data structure store** (BSD-3-Clause for open source) — **the lightweight coordination choice** . **Use cases**: **distributed locks via Redlock**, **leader election**, **rate limiting**, and **pub/sub**. **Redis 7.x** adds **Redlock-lite improvements** and better cluster support. **The trade-offs**: **weaker consistency guarantees than Raft-based systems**—Redis replication is asynchronous, so failover can lose writes . **Best for**: teams already using Redis who need lightweight coordination without a dedicated cluster.



- **CoreDNS**

  **DNS server that chains plugins** (Apache-2.0) — **the Kubernetes DNS standard** . **CoreDNS is the default DNS server for Kubernetes**—every service lookup flows through it. **Features**: **plugin-based architecture**, **service discovery for Kubernetes**, **caching**, **forwarding**, and **Prometheus metrics**. **Best for**: teams wanting DNS-based service discovery with a plugin ecosystem.



- **Eureka**

  **REST-based service discovery for AWS cloud** (Apache-2.0) — **the Netflix-originated choice** . **The service registry for Spring Cloud**—Netflix open-sourced it, and it remains the default registry for Spring Cloud applications. **The trade-offs**: **not actively developed since Netflix moved to other solutions**—Spring Cloud maintains it but doesn't recommend it for new projects. **Best for**: legacy Spring Cloud applications already using it.



- **Hazelcast**

  **In-memory data grid and distributed computing platform** (Apache-2.0 for open source) — **the distributed compute choice** . **Features**: **distributed maps, queues, and locks**, **near-cache**, **distributed executor service**, and **CP subsystem** based on Raft. **Best for**: teams needing distributed data structures alongside coordination.



- **Kuma**

  **Universal service mesh** (Apache-2.0) — **the mesh-native coordination choice** . **Built on Envoy** with **service discovery**, **health checking**, **mTLS**, and **traffic policies**. **Kuma 2.14** includes ongoing stability fixes for multi-zone federation, mTLS, and mesh policies . **Best for**: teams wanting coordination as part of a service mesh rather than a separate system.



### Additional Strong Open-Source Options



- **Apache Curator** — **ZooKeeper client with recipes** (Apache-2.0). Provides **leader election, locks, and barriers**—the standard wrapper for ZooKeeper.

- **Raft** — **Reference implementation of the Raft consensus algorithm** (Apache-2.0). The **foundation beneath etcd, Consul, and many others**.

- **Atomix** — **Distributed coordination framework** (Apache-2.0). Built on Raft, provides **distributed primitives** (maps, sets, locks) for Java.

- **JGroups** — **Reliable group communication toolkit** (Apache-2.0). The **cluster communication layer** beneath many Java distributed systems.

- Community **n8n** workflows for cluster alerting and leader election notification.



**Frameworks for building custom systems**: Combine **etcd** for Kubernetes-native configuration with **Consul** for service discovery, **ZooKeeper** for mature coordination primitives, **Redis** for lightweight locks, and **CoreDNS** for DNS-based discovery—creating a comprehensive distributed coordination stack.



## How to Contribute



1. Fork the repo.

2. Add/edit entries in `README.md` (follow existing format).

3. Include: name, link, 1–2 sentence description, and whether it's SaaS or open-source.

4. Submit PR with a short explanation.



Star the repo if you find it useful!



## Disclaimer



- This is a **community-curated** list — not exhaustive and not an endorsement.

- Distributed coordination systems handling cluster state must follow security best practices, including TLS, authentication, and backup procedures.

- **The "consensus vs. discovery vs. coordination primitives" distinction matters.** **etcd and ZooKeeper** provide **strong consistency via consensus**—leader election, locks, and configuration with linearizable reads . **Consul and CoreDNS** provide **service discovery**—finding services by name, with health checking . **Redis and Hazelcast** provide **lightweight coordination primitives**—locks and counters with weaker consistency guarantees . **Most production stacks use more than one**—Kubernetes runs on etcd, services discover each other via CoreDNS, and application-level locks might use Redis.

- **ZooKeeper 3.9's metrics and snapshot upgrades are significant.** **Pluggable metrics with Prometheus endpoint** address a long-standing observability gap . **Extended snapshot/restore commands** enable moving server state to new hosts without downtime . **For teams still running ZooKeeper, 3.9 is the upgrade to plan for.**

- **etcd is the Kubernetes dependency.** **If you run Kubernetes, you run etcd**—understanding its backup and restore procedures is not optional . **The trade-off**: etcd's Raft implementation is tuned for Kubernetes' write patterns—using it for high-throughput application data is a mistake.

- **Redis is not a consensus system.** **Asynchronous replication means failover can lose writes**—Redlock provides a best-effort distributed lock, not a guarantee . **If you need linearizable coordination, choose etcd, ZooKeeper, or Consul. If you need a fast lock for a non-critical path, Redis is fine.**

- **Eureka should not be adopted for new projects.** **Netflix stopped active development**, and Spring Cloud doesn't recommend it for new applications . **Consul and CoreDNS are the modern choices for service discovery.**

- Self-hosted open-source solutions require proper cluster management, backup strategies, and ongoing maintenance. **Coordination systems are the source of truth for distributed state**—losing them means losing cluster consistency.



---



**Made for platform engineers, SREs, and organizations building transparent distributed coordination solutions.**  

Let's make Distributed Coordination more open, data-driven, and consistent.
