# Chapter 21: Handling Overload

## Summary

This chapter addresses how to gracefully handle overload conditions in reliable serving systems. It covers strategies ranging from serving degraded responses to implementing sophisticated client-side throttling and criticality-based request prioritization. The key insight is that well-behaved backends should accept only requests they can process and reject the rest gracefully, rather than collapsing entirely under load.

## Key Concepts

- **Resource-based capacity modeling**: Measure capacity in actual resources (CPU cores, memory) rather than abstract "queries per second"
- **Per-customer limits**: Define quotas based on negotiated usage agreements, measured in resource units like CPU-seconds
- **Adaptive throttling**: Clients self-regulate by tracking acceptance rates and proactively dropping requests when backends are stressed
- **Criticality levels**: Standardized priority tiers (CRITICAL_PLUS, CRITICAL, SHEDDABLE_PLUS, SHEDDABLE) determine which requests to shed first
- **Utilization signals**: Local task-level measurements with exponential smoothing to prevent overreaction to traffic spikes
- **Retry budgets**: Systematic limits on retry attempts to prevent cascading failures

## Section Summaries

### The Pitfalls of "Queries per Second"

Measuring capacity by request count is fundamentally flawed because different queries consume vastly different resources, and these ratios change over time. CPU consumption works better as a provisioning signal.

### Per-Customer Limits

Services should allocate quotas based on negotiated agreements, measured in resource units like CPU-seconds per second. The total allocated capacity can exceed physical capacity because simultaneous maximum usage across all customers is statistically unlikely.

### Client-Side Throttling

Adaptive throttling tracks the ratio of total requests to accepted requests over a two-minute sliding window. When requests exceed accepts by a configured multiplier (typically 2x), clients begin probabilistically rejecting requests locally before sending them.

### Criticality Framework

Four standardized levels prioritize requests: CRITICAL_PLUS for the most severe user-visible operations, CRITICAL as the production default, SHEDDABLE_PLUS for batch jobs expecting partial unavailability, and SHEDDABLE for work tolerating frequent failures.

### Utilization Signals

Local utilization measurements protect individual tasks without requiring distributed coordination. The "executor load average" counts active and ready-to-run threads with exponential decay smoothing.

### Retry Mechanisms

Multiple safeguards prevent retry storms: a per-request limit of 3 attempts, a per-client budget capping retries at 10% of total traffic, and request metadata tracking retry counts.

## Practices

- Model capacity using actual resource consumption rather than request counts
- Implement per-customer quotas measured in resource units with negotiated limits
- Deploy client-side adaptive throttling to prevent clients from overwhelming stressed backends
- Tag all requests with standardized criticality levels and propagate through the call chain
- Use local utilization signals with smoothing to make task-level overload decisions
- Implement retry budgets at both per-request and per-client levels
- Return "don't retry" errors when widespread overload is detected
- Design backends to gracefully reject excess traffic rather than failing entirely

## Key Takeaways

1. **Graceful degradation is essential**: Well-behaved backends should accept only what they can process and reject the rest gracefully.

2. **Measure in resources, not requests**: CPU and memory consumption provide more accurate capacity signals than abstract request counts.

3. **Client cooperation is critical**: Adaptive throttling at the client level prevents wasted work during overload conditions.

4. **Standardize request priority**: A consistent criticality framework enables intelligent load shedding that protects important operations.

5. **Prevent retry storms systematically**: Multiple layers of retry limiting are necessary to prevent cascading failures.
