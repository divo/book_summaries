# Chapter 6: Monitoring Distributed Systems

## Summary
This chapter establishes foundational principles for monitoring and alerting in production systems, emphasizing the creation of monitoring systems that minimize noise while maximizing actionable signal. Written by Rob Ewaschuk and edited by Betsy Beyer, it argues that paging humans is expensive and should be reserved for genuinely urgent, actionable conditions affecting users.

## Key Concepts

- **Monitoring**: Collecting, processing, aggregating, and displaying real-time quantitative data about a system
- **White-box monitoring**: Internal metrics exposure through logs and instrumentation
- **Black-box monitoring**: Testing observable behavior as end users experience it
- **Alerts**: Human-directed notifications classified as tickets, email alerts, or pages
- **Symptoms vs Causes**: Distinguishing "what's broken" from "why it's broken"
- **The Four Golden Signals**: Latency, Traffic, Errors, and Saturation

## Section Summaries

### Why Monitor?
Organizations implement monitoring for six primary reasons: analyzing long-term trends, comparing performance across time periods, detecting active problems, building dashboards, conducting retrospective debugging, and supporting business analytics. The chapter emphasizes that paging a human is expensive, interrupting workflow or sleep, which justifies high thresholds for alert triggering.

### Setting Reasonable Expectations for Monitoring
Google's experience shows monitoring infrastructure requires dedicated engineering resources, with typical 10-12 person SRE teams allocating one to two members specifically to monitoring systems. The text advocates for simpler, faster monitoring systems with better post-incident analysis capabilities rather than complex predictive systems with intricate dependency hierarchies.

### Symptoms Versus Causes
The monitoring system should answer "what's broken?" (symptoms) and "why?" (causes) as two distinct questions. For example, HTTP 500 errors are symptoms while database connection refusal is a cause; slow responses are symptoms while CPU overload or network issues are causes.

### Black-Box Versus White-Box Monitoring
Black-box monitoring detects active problems already affecting users and represents symptom-oriented monitoring. White-box monitoring enables detecting imminent failures, masked issues, and root cause analysis through instrumentation access. Both approaches serve complementary purposes, and in a multilayered system, one person's symptom is another person's cause.

### The Four Golden Signals
If measurement resources are limited, focus on: **Latency** (time to service a request, distinguishing successful from failed request latency), **Traffic** (system demand in relevant units), **Errors** (rate of failing requests, whether explicit, implicit, or by policy), and **Saturation** (resource utilization emphasizing the most constrained resource). These four metrics provide essential visibility into user-facing system health.

### Worrying About Your Tail (or, Instrumentation and Performance)
Averaging can hide serious problems: with mean latency of 100ms across 1,000 requests per second, 1% of requests might take 5 seconds. Instead of tracking individual latencies, collect request counts bucketed by latency ranges using exponentially distributed histogram boundaries to visualize request distribution effectively.

### Choosing an Appropriate Resolution for Measurements
Different metrics warrant different collection frequencies based on their impact and the availability targets. CPU load requires minute-level granularity to detect spikes, while hard drive fullness checks can be infrequent for 99.9% availability targets. Internal server-side sampling with external aggregation reduces collection costs while maintaining useful granularity.

### As Simple as Possible, No Simpler
Monitoring systems risk becoming unwieldy through accumulated complexity. Rules catching real incidents should be simple, predictable, and reliable; rarely-exercised alerting (less than quarterly) warrants removal. The chapter warns against blending monitoring with profiling, debugging, logging, and load testing, advocating instead for distinct systems with clear, loosely coupled integration points.

### Tying These Principles Together
When creating monitoring rules, ask whether the alert detects an urgent, actionable condition affecting users, whether operators might ignore it, and whether the response could be automated. This leads to four principles: pages should permit urgency, every page must be actionable, pages require intelligence (robotic responses indicate automation opportunities), and pages should address novel problems.

### Monitoring for the Long Term
The Bigtable SRE example shows how excessive alerts based on mean performance obscured real problems; temporarily relaxing SLO targets created capacity to fix underlying infrastructure. The Gmail example demonstrates how individual task alerts generated unsustainable volumes, requiring tools for predictable human responses while planning proper fixes. Short-term availability through heroic effort breeds burnout; strategic short-term availability reductions often yield superior long-term stability.

## Practices

- Distinguish between symptoms (what's broken) and causes (why it's broken)
- Use black-box monitoring for active user-affecting problems, white-box for imminent failures and root cause analysis
- Focus on the four golden signals: Latency, Traffic, Errors, and Saturation
- Use histogram buckets for latency instead of averages to capture tail latency issues
- Choose measurement resolution appropriate to the metric's impact and SLO requirements
- Keep monitoring rules simple, predictable, and reliable
- Remove alerting rules that trigger less than quarterly
- Ensure every page is actionable and requires human intelligence
- Automate responses that become robotic or routine
- Consider long-term system health, not just immediate availability
- Allow short-term availability reductions to enable sustainable improvements

## Key Takeaways

1. **Paging is expensive**: Every page interrupts human workflow or sleep, so reserve alerts for genuinely urgent, actionable conditions that affect users.

2. **Focus on the Four Golden Signals**: Latency, Traffic, Errors, and Saturation provide the essential foundation for monitoring user-facing systems when resources are limited.

3. **Symptoms over causes for alerting**: Page on symptoms (what users experience) rather than causes; use white-box monitoring to diagnose root causes after symptoms are detected.

4. **Simplicity enables reliability**: Complex monitoring systems with intricate dependency hierarchies are harder to maintain and reason about; prefer simple, predictable rules.

5. **Long-term thinking prevents burnout**: Short-term heroics on fragile systems breed burnout; strategic investments in fixing underlying problems yield superior long-term stability and availability.
