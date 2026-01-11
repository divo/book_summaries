# Chapter 2: The Production Environment at Google, from the Viewpoint of an SRE

## Summary

This chapter provides an overview of Google's unique production environment architecture, covering hardware, system software, and supporting infrastructure that SREs work with daily. It establishes the context for understanding how Google's scale and infrastructure choices shape SRE practices and demonstrates how requests flow through the system using a Shakespeare search service example.

## Key Concepts

- **Borg**: Google's cluster operating system that manages job scheduling and resource allocation across machines
- **Colossus**: Google's distributed filesystem (successor to GFS) providing reliable, scalable storage
- **Bigtable**: A distributed sparse database built on Colossus for structured data storage
- **Spanner**: Google's globally distributed SQL database with strong consistency
- **Chubby**: A distributed lock service providing consensus and leader election
- **Borgmon**: Google's monitoring system for collecting and analyzing time-series data

## Section Summaries

### Hardware

Google's datacenters contain custom-designed machines optimized for their workloads. Machines are organized into racks, racks into clusters, and clusters into datacenters. Multiple datacenters form a campus, and campuses are distributed globally. This hierarchy influences how services are designed for fault tolerance and latency.

### System Software That Manages Hardware

Borg serves as the cluster operating system, handling job scheduling, resource allocation, and task management. Jobs describe the properties of tasks (binary, resources, constraints), and Borg handles placement, monitoring, and restart of failed tasks. This abstraction allows engineers to think about services rather than individual machines.

### Storage

Google's storage stack is layered: the lowest layer (D) provides block storage, Colossus provides distributed filesystem capabilities, and higher-level systems like Bigtable and Spanner provide structured data access. This layered approach allows different consistency and performance tradeoffs at each level.

### Networking

Google's network uses software-defined networking with a global backbone connecting datacenters. The network is designed for high bandwidth and low latency between datacenters, with sophisticated traffic engineering to optimize routing. Services communicate using Remote Procedure Calls (RPCs) with protocol buffers for serialization.

### Supporting Infrastructure

Chubby provides distributed locking and consensus, enabling leader election and configuration management. Borgmon collects time-series metrics for monitoring and alerting. These infrastructure services are foundational to building reliable distributed systems.

### The Shakespeare Service Example

The chapter walks through a request to search Shakespeare's works, demonstrating how requests flow from user devices through Google's frontend servers, load balancers, application servers, and storage backends. This example illustrates the practical application of all the infrastructure components discussed.

## Practices

- Design services to be location-independent, letting Borg handle placement
- Use distributed storage systems rather than local disk for durability
- Leverage RPC frameworks with built-in load balancing and health checking
- Build on infrastructure services like Chubby for coordination rather than implementing ad-hoc solutions
- Design for datacenter-level failures, not just machine failures
- Use protocol buffers for efficient, evolvable serialization

## Key Takeaways

1. **Abstraction enables scale**: By abstracting hardware details behind systems like Borg, engineers can focus on service logic rather than machine management.

2. **Layered storage provides flexibility**: The storage stack's layered design allows choosing appropriate consistency and performance tradeoffs for each use case.

3. **Infrastructure services reduce complexity**: Foundational services like Chubby and Borgmon provide battle-tested solutions for common distributed systems problems.

4. **Network is a first-class concern**: Google's software-defined network is designed as carefully as the compute and storage layers.

5. **Understanding the full stack matters**: SREs need to understand how all layers interact to effectively diagnose and resolve production issues.
