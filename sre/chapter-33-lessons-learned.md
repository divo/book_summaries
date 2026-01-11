# Chapter 33: Lessons Learned from Other Industries

## Summary

This chapter explores how Site Reliability Engineering principles manifest across various high-reliability industries beyond technology. The analysis reveals that while SRE principles are universal, their implementation varies significantly based on failure consequences and risk tolerance. Industries where human lives are at stake adopt more conservative approaches, while tech companies can leverage error budgets as innovation tools.

## Key Concepts

- SRE principles apply universally but implementation varies by industry context
- Risk tolerance directly correlates with velocity of change
- Defense-in-depth system design is common across all high-reliability industries
- Automation adoption varies based on industry maturity and failure consequences
- Cross-industry learning provides valuable insights for improving reliability practices

## Section Summaries

### Research Framework

The chapter addresses five central questions about whether SRE principles apply outside Google, how they manifest in other sectors, similarities and differences in implementation, factors driving variations, and lessons tech can learn from other fields. Nine industry veterans from defense, lifeguard services, medical devices, telecommunications, nuclear engineering, aviation, manufacturing, financial trading, and air traffic control were interviewed.

### Preparedness and Disaster Testing

Multiple industries emphasize proactive preparation through different mechanisms. The lifeguard industry uses "mystery shopper" scenarios, aviation employs realistic simulators, and the nuclear Navy conducts live drills two to three days per week. Key strategies include organizational focus on safety protocols, swing capacity, training and certification programs, defense-in-depth design, and detailed requirements gathering.

### Postmortem Culture

Industries adopt systematic investigation methods called Corrective and Preventative Action (CAPA), with regulatory bodies mandating these reviews. Manufacturing emphasizes "near miss" analysis, examining close calls before they become disasters.

### Automation Approaches

Industry perspectives on automation diverge significantly. Conservative sectors like the nuclear Navy and trading prefer human oversight. Efficiency-focused sectors like manufacturing embrace automation for consistency. The medical field uses automation to eliminate data-entry errors while maintaining safety.

### Risk Tolerance and Velocity Trade-offs

Google maintains higher velocity tolerance than industries where failures risk human lives, allowing tech to employ error budgets as innovation tools. Most traditional industries prioritize conservative approaches when safety is paramount.

## Practices

- Conduct regular disaster drills and simulations
- Maintain swing capacity (surplus resources) for handling emergencies
- Implement defense-in-depth system design
- Establish mandatory postmortem processes
- Analyze near misses systematically before they become actual failures
- Apply automation strategically based on failure consequences
- Use prescriptive playbooks and checklists for operational consistency
- Balance velocity against reliability based on specific risk profiles

## Key Takeaways

1. **Universal Principles, Context-Specific Implementation**: SRE principles apply across industries, but implementation must be tailored to failure consequences.

2. **Near Miss Analysis is Critical**: Examining close calls provides valuable learning opportunities often overlooked until catastrophe strikes.

3. **Automation Requires Careful Consideration**: The decision should be based on the specific risk profile of the industry.

4. **Error Budgets Enable Innovation**: In industries where human safety is not directly threatened, organizations can use error budgets for faster innovation.

5. **Cross-Industry Learning is Valuable**: Tech companies can improve reliability practices by studying industries with longer histories of managing high-reliability systems.
