# Chapter 20: Load Balancing in the Datacenter

## Summary

This chapter examines load balancing techniques within Google datacenters, focusing on distributing incoming query streams across homogeneous server processes called "backend tasks." The chapter covers the progression from simple round robin to weighted round robin policies, along with essential concepts like lame duck state and subsetting.

## Key Concepts

- **Backend tasks**: Homogeneous server processes that receive distributed query streams
- **The Ideal Case**: Perfect load distribution where all backend tasks consume identical CPU resources
- **Lame Duck State**: A quasi-operational state where backends can complete existing requests while refusing new ones during graceful shutdown
- **Subsetting**: Limiting the number of backends each client connects to (typically 20-100 tasks)
- **Capacity waste**: The gap between total available resources and usable resources due to uneven load distribution

## Section Summaries

### The Ideal Case

Perfect load balancing would result in all backend tasks consuming identical CPU resources simultaneously. In practice, significant capacity is wasted because traffic must be limited when the most-loaded task reaches capacity.

### Identifying Unhealthy Tasks - Flow Control

A basic approach tracks active request counts per backend connection, marking backends as unhealthy when the count reaches a configured limit. However, this only protects against extreme overload situations.

### Identifying Unhealthy Tasks - Lame Duck State

The lame duck state provides a robust mechanism for graceful shutdown, where backends notify clients to stop sending new requests while completing existing ones.

### Limiting Connections - Subsetting

Each client maintains a pool of persistent connections to a subset of backends. Random subsetting distributes load poorly, with significant variance between least-loaded and most-loaded backends.

### Deterministic Subsetting

Google's deterministic subsetting algorithm ensures nearly uniform connection distribution by shuffling backends differently per round and assigning consecutive subsets to clients within rounds.

### Simple Round Robin

Clients send requests sequentially through healthy, non-lame-duck backends, which still produces up to 2x CPU spread between least and most loaded tasks due to varying query costs and machine diversity.

### Weighted Round Robin

Backends include query rates, error rates, and CPU utilization in health check responses, allowing clients to adjust capability scores based on request handling efficiency. This approach significantly reduces CPU spread between tasks.

## Practices

- Implement lame duck state for graceful shutdown of backend tasks
- Use deterministic subsetting instead of random subsetting for uniform connection distribution
- Limit connection pool sizes to prevent resource waste (typically 20-100 backends per client)
- Include backend health metrics in health check responses
- Count recent errors as active requests to prevent traffic sinkholing to failing backends
- Configure appropriate lame duck timeout intervals based on typical request completion times

## Key Takeaways

1. **Naive approaches waste capacity**: Simple load balancing techniques can result in up to 2x CPU spread between tasks.

2. **Lame duck state enables graceful degradation**: Allowing backends to signal they're shutting down prevents dropped requests.

3. **Deterministic subsetting outperforms random**: Using a deterministic algorithm produces nearly uniform connection distribution.

4. **Client-side metrics are insufficient**: Least-loaded round robin fails because clients only see their own requests.

5. **Weighted round robin with backend metrics is most effective**: Having backends report their actual utilization enables intelligent load distribution.
