# Chapter 30: Embedding an SRE to Recover from Operational Overload

## Summary

This chapter addresses a critical challenge for SRE teams: when operational work overwhelms project time, temporarily embedding an SRE into an overloaded team can restore balance. Rather than simply helping clear tickets, the embedded engineer focuses on systemic improvements through observation, documentation, and recommendations.

## Key Concepts

- **Ops Mode**: A reactive state where teams respond to issues by adding more administrators rather than reducing workload
- **Bad Apple Theory**: The flawed belief that removing individual mistakes will eliminate problems
- **Kindling**: Emerging problems that haven't yet caused outages but represent latent risks
- **Toil vs. Necessary Overhead**: Distinguishing between work that can be automated and work that is inherently required
- **Blameless Postmortems**: Analysis focused on systemic causes rather than individual fault

## Section Summaries

### Phase 1: Learning Context

The embedded SRE must first understand why the team operates in "ops mode." This involves shadowing on-call sessions, identifying major stress sources, and recognizing emerging problems ("kindling") such as knowledge gaps and overlooked dependencies.

### Phase 2: Sharing Context

Rather than critiquing past postmortems, the embedded engineer should author the next one to demonstrate blameless analysis techniques. The chapter explicitly rejects the "Bad Apple Theory." By organizing fires into "toil" versus necessary overhead, the team can clarify what requires automation.

### Phase 3: Driving Change

Starting with Service Level Objectives (SLOs) provides quantitative grounding for prioritization. The embedded SRE should guide team members through permanent solutions while reviewing their work, rather than fixing issues personally. The engagement concludes with an after-action report.

## Practices

- Shadow on-call sessions to understand the true nature of operational burden
- Prioritize outages by their impact on team morale, not just business metrics
- Identify "kindling" - latent risks that haven't yet caused outages
- Author postmortems rather than critiquing existing ones
- Categorize work into toil (automatable) versus necessary overhead
- Establish SLOs as the foundation for decision-making
- Guide team members to solutions rather than implementing fixes directly
- Use leading questions to develop critical thinking
- Document the engagement in an after-action report

## Key Takeaways

1. **Systemic improvement over individual fixes**: The goal is lasting improvements that prevent operational overload from recurring.

2. **Teaching over doing**: Guiding team members creates sustainable capability and ownership.

3. **SLOs as decision framework**: Quantitative objectives provide grounding for prioritization decisions.

4. **Blameless culture enables learning**: Focusing on systemic causes creates an environment where teams can identify root causes.

5. **Recognize kindling before it ignites**: Proactively identifying latent risks prevents future crises.
