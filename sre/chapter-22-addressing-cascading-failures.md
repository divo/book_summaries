# Chapter 22: Addressing Cascading Failures

## Summary

A cascading failure is a failure that grows over time as a result of positive feedback, where one component's failure increases the likelihood that other components will also fail. This chapter provides comprehensive guidance on understanding, preventing, and responding to cascading failures in distributed systems.

## Key Concepts

- **Cascading Failure**: A failure that propagates through a system via positive feedback loops
- **Resource Exhaustion**: The depletion of CPU, memory, threads, or file descriptors that triggers cascading problems
- **GC Death Spiral**: A destructive cycle in garbage-collected languages where memory pressure causes excessive GC cycles
- **Load Shedding**: Deliberately dropping traffic as a server approaches overload
- **Graceful Degradation**: Reducing service quality rather than failing completely
- **Retry Amplification**: Exponential growth of load when naive retry logic is implemented across multiple layers
- **Deadline Propagation**: Passing deadlines through the call stack rather than creating new ones at each layer

## Section Summaries

### Causes of Cascading Failures

Server overload is the most common trigger, typically occurring when infrastructure capacity becomes insufficient. Resource exhaustion manifests in multiple interconnected forms: CPU, memory, threads, and file descriptors.

### Prevention Strategies

Load testing helps understand actual breaking points. Queue management with small queue lengths allows servers to reject requests early. Load shedding drops traffic as the server approaches overload. Graceful degradation reduces quality rather than failing completely. Capacity planning based on realistic failure scenarios reduces risk.

### Retry Management

Retry logic must use randomized exponential backoff, limit retries per request, implement server-wide retry budgets, use distinct error codes for retriable versus permanent failures, and avoid retry amplification across system layers.

### Deadline Propagation

Systems should propagate deadlines set high in the stack rather than inventing new deadlines at each layer. This ensures servers don't waste resources processing requests that have already exceeded their time limits.

### Emergency Response

Tactical options include increasing resources, disabling health checks temporarily, restarting wedged servers, dropping traffic, degrading service quality, eliminating batch operations, and blocking malicious queries.

## Practices

- Always use randomized exponential backoff when scheduling retries
- Test components to their breaking point to understand failure behavior
- Maintain queue lengths at approximately 50% or less of thread pool capacity
- Implement both load shedding and graceful degradation mechanisms
- Propagate deadlines through the call stack
- Use distinct error codes for retriable versus permanent failures
- Implement server-wide retry budgets
- Prevent backend servers from proxying requests to each other
- Pre-engineer degradation pathways for emergency activation

## Key Takeaways

1. **Positive feedback loops are the enemy**: Breaking these loops through proper retry management, deadline propagation, and load shedding is essential.

2. **Know your breaking points**: Load testing to failure is crucial for understanding system limits.

3. **Something must give under overload**: Design systems to fail gracefully by implementing load shedding and degradation pathways.

4. **Retry logic is critical and dangerous**: Naive retry implementations can exponentially amplify problems.

5. **Resource exhaustion cascades**: CPU, memory, threads, and file descriptors are interdependent.
