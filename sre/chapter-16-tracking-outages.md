# Chapter 16: Tracking Outages

## Summary

This chapter examines how Google SRE uses systematic outage tracking to improve service reliability over time. The core principle is that organizations cannot enhance reliability without establishing baseline measurements and continuously monitoring progress against them. Google accomplishes this through two key systems: Escalator for alert notifications and Outalator for comprehensive outage tracking and analysis.

## Key Concepts

- **Baseline measurement**: You cannot improve what you do not measure
- **Alert escalation**: Automated escalation ensures alerts are acknowledged and addressed within configured timeframes
- **Alert aggregation**: Combining related notifications into single incident records reduces noise
- **Tagging and annotation**: Free-form metadata with hierarchical namespacing enables consistent categorization
- **Multi-layer analysis**: Moving from basic statistics to comparative analysis to semantic understanding of root causes
- **Cross-team visibility**: Tracking systems can reveal incidents affecting services even when teams don't receive direct alerts

## Section Summaries

### The Escalator

Google employs a centralized alert notification system that tracks human acknowledgment of alerts. When acknowledgments are not received within configured timeframes, the system automatically escalates notifications to secondary contacts.

### Outalator: The Outage Tracker

Outalator serves as Google's primary outage tracking system, receiving passive copies of all monitoring system alerts. It enables annotation, grouping, and analysis of alert data to identify patterns and trends.

### Queue Management

The system displays time-interleaved notifications from multiple alert queues simultaneously, eliminating the need to manually switch between separate channels.

### Alert Aggregation

Multiple related notifications are combined into single incident records, which proves essential for complex failures where a single root cause triggers alerts across multiple teams.

### Tagging System

A tagging system applies free-form metadata using hierarchical namespacing (e.g., "cause:network:switch") to categorize incidents. Team-specific tag suggestions promote consistency while maintaining flexibility.

### Analysis and Reporting

The tool operates across multiple analytical layers: foundation-level counting and aggregate statistics, comparative analysis across teams and time periods, and semantic analysis identifying infrastructure components causing disproportionate incidents.

## Practices

- Implement automated escalation for unacknowledged alerts
- Aggregate related alerts into unified incident records
- Use hierarchical tagging conventions across teams
- Generate regular reports including shift handoff summaries and weekly production reviews
- Enable cross-team visibility to reveal hidden dependencies and impacts
- Track beyond incidents for audit trails and privileged access logging
- Analyze at multiple levels beyond simple counting

## Key Takeaways

1. **Measurement is foundational**: Organizations cannot improve reliability without systematic tracking of incidents and their patterns over time.

2. **Aggregation reduces noise**: Combining related alerts into single incidents prevents alert fatigue and provides clearer context.

3. **Consistent tagging enables analysis**: Hierarchical, team-standardized tagging transforms raw incident data into queryable intelligence.

4. **Cross-team visibility reveals hidden impacts**: Tracking systems can expose incidents affecting services even when direct alerts are not received.

5. **Strategic value emerges from systematic tracking**: Beyond immediate incident management, comprehensive tracking enables recognition of systemic issues.
