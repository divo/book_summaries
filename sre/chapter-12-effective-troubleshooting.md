# Chapter 12: Effective Troubleshooting

## Summary

This chapter by Chris Jones presents troubleshooting as a learnable, systematic skill essential for SREs operating distributed systems. It introduces the hypothetico-deductive method as the foundation for troubleshooting and provides a structured process model: Problem Report, Triage, Examine, Diagnose, Test/Treat, and Cure. The chapter emphasizes that expertise develops through understanding both how systems should work and why they fail, and that systematic approaches bound recovery time better than relying on intuitive expertise alone.

## Key Concepts

- **Hypothetico-deductive method**: Observe problems, combine observations with system knowledge, generate hypotheses, and iteratively test through evidence comparison or controlled modifications
- **Troubleshooting process model**: Problem Report -> Triage -> Examine -> Diagnose -> Test/Treat -> Cure
- **"Horses not zebras"**: Prefer simpler explanations while acknowledging correlation doesn't establish causation
- **System inertia**: Systems tend to remain stable; recent changes are productive starting points for investigation
- **Negative results are valuable**: Failed experiments inform others' work and prevent duplicated effort

## Section Summaries

### Core Theory

The chapter introduces the hypothetico-deductive method as the scientific foundation for troubleshooting distributed systems. It emphasizes iteratively generating and testing hypotheses by comparing observations against expected behavior or through controlled system modifications.

### Common Pitfalls

Four frequent troubleshooting errors are identified: misinterpreting metrics, misunderstanding system changes, generating implausible theories, and chasing spurious correlations. The chapter reminds practitioners to prefer simpler explanations while being cautious about confusing coincidence with causation.

### Problem Reports

Effective problem reports should specify expected behavior, actual observed behavior, and reproduction steps when possible. Google practice emphasizes consistent formatting and searchable storage through bug-tracking systems.

### Triage

This critical phase involves assessing severity and prioritizing response, with major outages demanding immediate mitigation before root-cause analysis. The overriding principle is to stabilize the system first.

### Examine

Diagnosis requires visibility into system behavior through metrics/time-series data, logging infrastructure with multiple verbosity levels, and request tracing tools. The text advocates for statistical sampling in high-traffic services.

### Diagnose

This phase involves simplification and reduction through component testing, divide-and-conquer approaches to isolate problems, and asking "what," "where," and "why" questions. Recent changes analysis is particularly productive since systems exhibit inertia.

### Test and Treat

Once hypotheses are narrowed, experimentation determines causation through tests designed with mutually exclusive alternatives. Testing should prioritize probable causes before unlikely ones and account for confounding factors.

### Cure

After identifying probable causes, documentation consolidates findings including what malfunctioned, investigation methods, resolution approach, and prevention measures. This becomes the postmortem.

## Practices

- Use consistent, searchable formatting for problem reports
- Stabilize the system before conducting root-cause analysis during major outages
- Implement multiple logging verbosity levels adjustable without restarts
- Use statistical sampling for high-traffic services to reduce logging overhead
- Build request tracing capabilities to follow individual requests through the entire stack
- Test components with known inputs in non-production environments
- Use divide-and-conquer or bisection approaches to isolate problems systematically
- Document all hypotheses, tests executed, and results
- Publish negative results to prevent duplicated effort across teams

## Key Takeaways

1. **Troubleshooting is a learnable skill**: Systematic approaches, taught and learned through practice, bound recovery time better than relying on intuitive expertise alone.

2. **Stabilize before investigating**: During major outages, the priority is to mitigate impact before diving into root-cause analysis.

3. **Recent changes are primary suspects**: Systems exhibit inertia, so recent deployments and configuration modifications are the most productive starting points.

4. **Built-in observability is essential**: White-box metrics, structured logging, and request tracing should be included in every component from inception.

5. **Document everything, including failures**: Negative results resolve design questions definitively and accelerate collective learning.
