# Chapter 10: Practical Alerting

## Summary

This chapter explores Borgmon, Google's internal time-series monitoring system that evolved from traditional check-based alerting into a sophisticated data collection and rule evaluation platform. By treating metrics as first-class data sources with algebraic expressions, Borgmon enabled monitoring to scale independently of service size while reducing maintenance burden through abstraction and reusability. The principles established by Borgmon now underpin popular open-source monitoring systems like Prometheus, Riemann, and Bosun.

## Key Concepts

- **White-box monitoring**: Inspecting internal service state through standardized data exposition rather than executing custom scripts
- **Time-series data model**: Labeled (timestamp, value) pairs organized chronologically with multidimensional labels
- **Varz interface**: HTTP endpoints exposing metrics in a simple space-separated key-value format
- **Rule evaluation**: Algebraic expressions that query and transform time-series data
- **Aggregation**: Summing rates across tasks to treat entire jobs as monitoring units
- **Synthetic variables**: Auto-generated metrics tracking target resolution, response, and health status
- **Hierarchical monitoring**: Multi-tier Borgmon structures for scalable data collection and aggregation

## Section Summaries

### Monitoring Fundamentals

Monitoring serves as the foundation for stable services, enabling data-driven decisions about changes and measuring alignment with business objectives. At Google's scale, alerting on individual machine failures creates excessive noise, so systems aggregate signals to identify meaningful patterns instead.

### The Rise of Borgmon

Borgmon emerged around 2003 to complement Borg (Google's job scheduler), adopting white-box monitoring through standardized HTTP endpoints rather than custom check scripts. This approach enabled efficient mass collection without subprocess overhead and created a common language for instrumentation across services.

### Instrumentation and Data Collection

Applications export metrics through the `/varz` HTTP endpoint using a simple textual format with space-separated key-value pairs. This low barrier to instrumentation drove widespread adoption, though it required careful change management to maintain compatibility. Borgmon automatically tracks synthetic variables indicating target availability, making it easy to detect when monitored tasks become unreachable.

### Time-Series Storage and Structure

Data is stored in an in-memory database with regular disk checkpoints, using labels (`key=value` pairs) to create multidimensional structures. Essential labels include `var` (variable name), `job` (server type), `service` (job collection), and `zone` (datacenter location). A configurable "horizon" (typically 12 hours) governs garbage collection, with older data archived to an external Time-Series Database (TSDB).

### Rule Evaluation

Borgmon operates as a "programmable calculator" enabling algebraic expressions across time-series data with temporal history queries. The `rate()` function computes deltas over specified time windows, essential for counter-based metrics, while filtering and grouping operations manipulate label dimensions. Rules can aggregate per-task metrics into cluster-wide views, such as calculating error ratios by summing errors across instances and dividing by total requests.

### Alerting Mechanics

Alerting rules evaluate to boolean values and require minimum durations (typically two evaluation cycles) before triggering to prevent "flapping" from rapid state changes. The Alertmanager service handles alert routing, inhibition, deduplication, and fan-in/fan-out based on label patterns. Templated alert messages provide contextual information to help responders quickly understand the issue.

### Monitoring Topology and Sharding

Large deployments use hierarchical Borgmon structures with global, datacenter-level, and scraping layers to avoid collection bottlenecks. Upper-tier systems receive filtered data from lower tiers using a binary protocol, reducing network overhead compared to the text-based varz format. This topology enables consistent monitoring regardless of service size.

### Black-Box Monitoring Complement

While Borgmon provides white-box monitoring of internal state, Google uses Prober for black-box validation of external service behavior and payload correctness. Prober can detect failures invisible to white-box systems, such as DNS errors preventing requests from reaching backends. Monitoring both frontend domains and backend servers enables precise failure localization.

### Configuration Management

Borgmon separates rule definitions from monitored targets, enabling rule reuse across multiple systems through language templates (macros). Two configuration classes emerged: schema codification (templates for standard variable exports) and aggregation libraries (generic rules for data flows). Continuous integration services test configurations, validate syntax, and deploy safely to production.

## Practices

- Expose metrics via standardized HTTP endpoints rather than custom check scripts
- Use labeled time-series with consistent naming conventions for flexible querying and aggregation
- Calculate rates over time windows rather than relying on instantaneous values
- Aggregate metrics at the job level to reduce noise from individual instance variations
- Require minimum alert durations (at least two evaluation cycles) to prevent flapping
- Separate rule definitions from targets to maximize configuration reuse
- Use templates/macros for common patterns to reduce repetition and bugs
- Combine white-box and black-box monitoring to detect different failure modes
- Implement hierarchical collection for large-scale deployments to avoid bottlenecks
- Track synthetic variables for target availability to detect monitoring failures
- Test monitoring configurations through CI before production deployment

## Key Takeaways

1. **White-box monitoring scales better than check scripts**: Standardized metric exposition through HTTP endpoints enables efficient mass collection and creates a common instrumentation language across services.

2. **Time-series as first-class data sources**: Treating metrics as queryable, labeled data structures with algebraic operations enables powerful aggregation and reduces the gap between data collection and alerting.

3. **Aggregation reduces noise at scale**: Alerting on individual machine failures is ineffective at scale; aggregate metrics (error rates, request counts across clusters) provide more meaningful signals.

4. **Configuration abstraction enables reuse**: Separating rules from targets and using templates/macros for common patterns reduces maintenance burden and promotes consistency.

5. **Black-box and white-box monitoring are complementary**: White-box monitoring shows internal state while black-box testing validates external behavior; both are needed to detect the full range of failure modes.
