# Chapter 25: Data Processing Pipelines

## Summary

This chapter examines the challenges of managing complex data processing pipelines at scale, contrasting periodic pipelines (scheduled batch jobs) with continuous pipelines (perpetually running systems). It introduces Google's Workflow system as a superior model that provides exactly-once semantics, strong correctness guarantees, and business continuity.

## Key Concepts

- **Pipeline Design Pattern**: Originated from co-routines and Unix pipes, became prominent with "Big Data"
- **Simple vs Multiphase Pipelines**: Single-stage vs chained programs processing data sequentially
- **Continuous vs Periodic Processing**: Always-running systems vs scheduled batch executions
- **Exactly-Once Semantics**: Guarantee that each piece of data is processed exactly once
- **Leader-Follower Pattern**: Distributed systems architecture with a master coordinating workers
- **System Prevalence**: Keeping system state in memory with disk journaling for persistence

## Section Summaries

### Challenges with Periodic Pipelines

Uneven work distribution creates completion delays. Hanging chunks can halt entire pipeline progression. Cluster resource constraints create scheduling delays. Periodic pipelines only emit metrics upon completion, making failed jobs invisible. Thundering herd problems occur when workers start simultaneously.

### Google Workflow: A Superior Model

Developed in 2003, Workflow implements the leader-follower pattern combined with system prevalence. This architecture enables exactly-once semantics at massive scale.

### Architecture as Model-View-Controller

The Model (Task Master) maintains all job state in memory with synchronous disk journaling. Workers serve as the View, operating as stateless processors. An optional Controller manages scaling and snapshotting.

### Correctness Guarantees

Workflow provides four overlapping mechanisms: configuration tasks create barriers, work commits require valid worker leases, output files receive unique names, and server tokens validate Task Master identity.

### Business Continuity

Task Master journals are stored in Spanner, with Chubby providing distributed lock service for writer election. Redundant local Workflows run in distinct clusters with heartbeat mechanisms.

## Practices

- Design for continuous processing rather than periodic batch jobs when possible
- Implement checkpointing to avoid wasting computational work when jobs fail
- Use unique output file naming to prevent data corruption from orphaned processes
- Implement lease validation to ensure workers cannot commit stale updates
- Store critical state in distributed databases for cross-datacenter resilience
- Use distributed lock services for leader election
- Run redundant systems in distinct clusters to survive datacenter failures
- Implement heartbeat mechanisms for automatic failover detection
- Provide real-time telemetry rather than only emitting metrics on job completion

## Key Takeaways

1. **Periodic pipelines have hidden costs**: Batch-oriented pipelines suffer from uneven work distribution, hanging chunks, and poor observability.

2. **Continuous pipelines are often more reliable**: Despite appearing more complex, continuous processing systems with proper design produce more dependable results.

3. **Correctness requires multiple overlapping guarantees**: Exactly-once semantics at scale requires defense in depth.

4. **Business continuity needs active design**: Resilience across datacenter failures requires intentional architecture.

5. **Real-time observability matters**: Systems that only report metrics upon completion leave operators blind during failures.
